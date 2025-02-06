<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Car Booking</title>
    <style>
        /* General Styling */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Helvetica Neue', Arial, sans-serif;
            background-color: #f4f4f4;
            color: #333;
        }

        /* Car Section Styling */
        .car-section {
            background-color: #fff;
            padding: 60px 20px;
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            text-align: center;
        }

        .section-title {
            font-size: 2.5rem;
            font-weight: bold;
            color: #007bff;
            margin-bottom: 40px;
            text-transform: uppercase;
        }

        /* Car Items Styling */
        .car-list {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            gap: 30px;
        }

        .car-item {
            background-color: #f9f9f9;
            border-radius: 12px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            padding: 20px;
            width: 30%;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .car-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
        }

        .car-image {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 8px;
        }

        .car-name {
            font-size: 1.6rem;
            font-weight: bold;
            color: #333;
            margin: 15px 0;
        }

        .car-description {
            font-size: 1.1rem;
            color: #666;
            margin-bottom: 10px;
            text-align: justify;
        }

        .car-price {
            font-size: 1.4rem;
            color: #007bff;
            font-weight: bold;
            margin: 10px 0;
        }

        .car-button {
            background-color: #007bff;
            color: white;
            padding: 10px 20px;
            font-size: 1rem;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.2s;
        }

        .car-button:hover {
            background-color: #0056b3;
            transform: scale(1.05);
        }

        .booking-message {
            background-color: #4CAF50;
            color: white;
            padding: 20px;
            margin-top: 30px;
            text-align: center;
            border-radius: 8px;
            font-size: 1.2rem;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            animation: fadeOut 5s forwards;
        }

        @keyframes fadeOut {
            0% { opacity: 1; }
            80% { opacity: 1; }
            100% { opacity: 0; display: none; }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .car-list {
                flex-direction: column;
                align-items: center;
            }

            .car-item {
                width: 80%;
                margin-bottom: 30px;
            }

            .section-title {
                font-size: 2rem;
            }
        }

    </style>
</head>
<body>

    <section id="cars1" class="car-section">
        <div class="container">
            <h2 class="section-title">Premium Cars for Your Tour</h2>
            <div class="car-list">
                <!-- Car Item 1 -->
                <div class="car-item">
                    <img src="https://images.pexels.com/photos/3778776/pexels-photo-3778776.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" alt="Luxury Car" class="car-image">
                    <h3 class="car-name">Luxury Sedan</h3>
                    <p class="car-description">A premium sedan for a comfortable ride on your luxury tour.</p>
                    <p class="car-price">$150/day</p>
                    <button class="car-button">Book Now</button>
                </div>

                <!-- Car Item 2 -->
                <div class="car-item">
                    <img src="https://images.pexels.com/photos/1429775/pexels-photo-1429775.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" alt="SUV" class="car-image">
                    <h3 class="car-name">SUV</h3>
                    <p class="car-description">Perfect for groups and family tours with extra space and comfort.</p>
                    <p class="car-price">$100/day</p>
                    <button class="car-button">Book Now</button>
                </div>

                <!-- Car Item 3 -->
                <div class="car-item">
                    <img src="https://images.pexels.com/photos/3972755/pexels-photo-3972755.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" alt="Sports Car" class="car-image">
                    <h3 class="car-name">Sports Car</h3>
                    <p class="car-description">For those who love adventure and speed on their tours.</p>
                    <p class="car-price">$200/day</p>
                    <button class="car-button">Book Now</button>
                </div>
            </div>
        </div>
    </section>

    <script>
       document.addEventListener("DOMContentLoaded", function () {
            const buttons = document.querySelectorAll(".car-button");
            const bookedCars = new Set(); // Set to track booked cars

            // Function to handle car booking
            function handleCarBooking(event) {
                const button = event.target;

                // Check if the car is already booked
                const carName = button.parentElement.querySelector('.car-name').textContent;
                if (bookedCars.has(carName)) {
                    // Show a unique message for already booked cars
                    showBookingMessage(`The ${carName} is already booked.`);
                    return;
                }

                // Disable the button to prevent multiple clicks
                button.disabled = true;
                
                // Change the button text to "Booked"
                button.textContent = "Booked";

                // Add the car name to the booked cars set
                bookedCars.add(carName);
                
                // Show a success message
                showBookingMessage(`Your ${carName} has been successfully booked. Enjoy your tour!`);
            }

            // Function to display booking success message
            function showBookingMessage(message) {
                const messageContainer = document.createElement("div");
                messageContainer.classList.add("booking-message");
                messageContainer.textContent = message;
                document.body.appendChild(messageContainer);

                // Automatically remove the message after the animation ends (5 seconds)
                setTimeout(() => {
                    messageContainer.remove();
                }, 5000);
            }

            // Attach the event listener to each button
            buttons.forEach(button => {
                button.addEventListener("click", handleCarBooking);
            });
        });
    </script>

    <section id="cars2" class="car-section">
        <div class="container">
            <h2 class="section-title">Affordable Cars for Your Tour</h2>
            <div class="car-list">
                <!-- Car Item 1 -->
                <div class="car-item">
                    <img src="https://static1.topspeedimages.com/wordpress/wp-content/uploads/2023/09/2023-honda-civic-sedan-1.jpg" alt="Economy Sedan" class="car-image">
                    <h3 class="car-name">Economy Sedan</h3>
                    <p class="car-description">A reliable and budget-friendly sedan for your everyday needs.</p>
                    <p class="car-price">$40/day</p>
                    <button class="car-button">Book Now</button>
                </div>

                <!-- Car Item 2 -->
                <div class="car-item">
                    <img src="https://images.pexels.com/photos/1429775/pexels-photo-1429775.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" alt="Compact SUV" class="car-image">
                    <h3 class="car-name">Compact SUV</h3>
                    <p class="car-description">Perfect for small families or groups, offering more space at an affordable price.</p>
                    <p class="car-price">$55/day</p>
                    <button class="car-button">Book Now</button>
                </div>

                <!-- Car Item 3 -->
                <div class="car-item">
                    <img src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxMTEhUTExIVFhUXGBUXFxgYGRYdGhcYFxUXFxcXGBgYICgiGx0lHRcWITEiJSkrLi4uFx8zODMtNygtLisBCgoKDg0OGhAQGy8mHyUtLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLf/AABEIAKgBLAMBIgACEQEDEQH/xAAbAAABBQEBAAAAAAAAAAAAAAAEAQIDBQYAB//EAEoQAAEDAgMDCQQHBgMFCQAAAAECAxEAIQQSMQVBUQYTImFxgZGhsTLB0fAHQlJygpLhFDNiosLxI0SyFhdDY9IVJDRTVHOjs+L/xAAaAQADAQEBAQAAAAAAAAAAAAAAAQIDBAUG/8QALhEAAgIBAwMDAwMEAwAAAAAAAAECEQMSITEEQVEFEyJhkfAUoeEycYHBIzNS/9oADAMBAAIRAxEAPwDIBNKEVOG6eGjwr6ij5JzBwinBNEBg1KnDU9hW2CBFOCKNThqmTheqlaDTJlaGzTwzVonDU/mbgcaWtD9tlYMNSjC9lWwYpMXhRkJEyLgjWRpbf2VMslIuOG3RW/shppajhUStorVKCUJvBJCtOPlHbXJ2y2EAb7kmLECdBc8Na5v12O6ujofQTJwzT/2U0mHxjaukQTAgcU8Tupz+0G0xCs5m56jxIEAdmsVX63HV2hfoZXVHDDHhTkNjSb0xva43g6bhqarsbiCsybeR+e+uXP6tihG47vwbYvTZN/LYlxe0C2ooubWO6euI8qGRjnDBKr9Q1+NR80BcqM9ZmuUwRe8efxrw8/qWWb+LpHqY+mxwXG4j2ZUlR17vS9CIN7QPWiAJHz76hUwdY7ybedcMsspu5M34FKD+pn5FdlPE9wA/vUKiscLb5Jpv7RPtXHl5xSphY3EW3j30O08dArw/Si3VpUJCR26+sVCG075I7THgLVUXtuIRTSjvpWcLf59BSKfBslSfWpmlJiCvMeAvQ3IAtDaRcqHj7qjddG5fgB8+dM/Zyv6oA4kyfC9CYvCEDUnyHnURir3YzsUsb1ecmq55xI4ntNRuJUbTHZf0qNaAnXMfAfrXXCCQiZGL+ympRilbyB2RVYt0i4EfPGpG1GtHjQBq1JN5JPfQi8SBYD57BXGd9u2h3ge2nCCGEt4gn9BUhUePjQTU7hUkL4Ed1NwViClHr+e2hzHz/ekUDF799MSo/IFNRA9ZGGp4w1WycPTxhvm9fTe4fP8AtFSnC1KnDVajD1InD0nkKWIrEYWpEYeiMc+lkBStCQJtaTr2UONotLsF5SUzI1ANp+dKzlnSdNmkcD5oDcxKWlEOE6WNrkbh3GmvvZCFK0zAhUfVIEjqrO4x9a1KCnAsZrxAJ3jXsiRQ4x6koKTBno6SQB56H0rzZ+pJPg7Y9Gi1xW3VKVKIyiRp2VXr2kpdyo2tbQXmLHs8Kibwqk3BJGt/eBpQDjhLoQk5tSrXKnh1zXlz6vLkb+Wx1xwwjwgzm4MgEzO/UnhPz50reFAEx5/PXUuASlV7mLd/VfT1otxoG0EW6jHdFq5JZnwaAqWLax1AwP1p5TbSY0HCp2nCiRKYHAT508vyLQeyazeSXAAuVWtuwXNMdiPZlX8R+Y8RXIdK1wLxrw/lpFOwrQHsv3QbCkrECIdIMkpB6jp4SaNaxRNh3mwn3HxoV9RIlISB3E9ltKbhQVCy4+bg6iqatAWCu2T1DT80eVA454IuekeG7zo4YJMajMeJ+AoY7MEEKEnqB7t9RBxT3EAMYxtR6cjvj118Ka8whSuh47vEih8Rs4JVITI4Sm3jNHtOpyiGvMx7hXQ6W8RisYZyLZeq9/KRVdtFB+u4LbgBPnFGp2mEKIDYP4Z8zNI9iFuiCEJ6sw9E0o6lK2gM8twaAqJ6/k1Z4EBIElJ759KhVsVaj0Ez16DxMU5Oy3E2UsJ6pBPgK6JSi1ViLBe0leyFd8RXN4bOZLg8CfcPWoWNjlZu4uepKk+Zo1GxMt85n+K58b1zy0R4e/8AYY5zYaTotavygepNV2N2aEg6A9ZP9IFHreKRCVk9pEeWlDLwrq5HoVH0FEJS7sRm30GY17j6mpMOwo7vEwKtHNiOA+yR1kH3kVM1s9waD8vNjzM11vMq2YwZrBHgnuzH3Cp/2AniTwCRPvq5weAURee9Z9EJ99GJ2MBcwe5Z9TXJLNTAoUYDcoHvI9BFRvbO6wK0TuBRGoHcgUJiGLWk9l/9NJZXYGZfw0aqHj7r0LzSOvwNaJ/Ar1yHzH+oVCnCucQO1X/6rojm2A9Uwu1WVBJBVcAxlJ1mJyzGhF+HZVshtMSIjWa8dwpWAOA1G6d9uzfWm2Ztp5ptSQEwo6krMaRlGiRG6JMkm5r0o9eq+ZzPpvBvyhI1jq0v2UBj9pNISTZQBgieoSOo9IeBrGP7cfuFqCgQE5YFxeCOsazPpQRVKrqM3IkzJ7SL2H61lP1JV8UOPT+Sy2jtlS8yLlBkCd1+jpv014ms9iswJKelN+u5k6bvdRNkuEFUzPRGhsLC80LjcKpcoBIIMg7tbQdIt5V58s0sj+TOhJLghS4kqIWZMQm0z1SKIwzyyQgdFMibkyRfjSYTCZFFSib9ESEkzoBI0kcONOawiA4FFeUdIg5gBJGgzSNKzbRQdi0yrLqm++I7tDQCNnq5yUquQZ104kmPKtZhdhJypXiHCgHQFQBPapWpi+UBREiwqdOKwDfsoU51hC1juU4Ux+Wt8PR5Zrx+fngylkSKFKEoAGcGI0g3463NKFpUd53kx6iDPjV+OUjQ9jCrItMqaGu792b99EJ23gnE5XZZXuCxmSQOC20gDhcCtn6W0rcn9v5IWdN1t9zKut2lUBO6JHiNB3VE8/mByISpAmVEj3SfOpeUOz3UOpIdRzC7pU4pISkxmylREQR7J36dsTKikQMXhkjgl9uPALFQvTWuZL9x+43wiJrFJynIlJjUFRSPCb0QlnnmyUpAPd+sVEW2Zk4jCk7zLZPkq9T4LBZkucy+lYQEKORslAzFQ6ZQej7JMwTANqcvTv8AzNfuPXLuilRLZI87+pNPw+PSF3CiZ1m3lFW7OLacJSX2ZFv8QhKT2KUSlQpMTh8O2nOUYVwz9QYdYHCcpSryql6fJ/1Nf4/mhe59AYbcWNAI6+j5kiaMZZDsEhPd0vO8UXs57DPwkYVlKtAedDRVO5IMie41bP7NygQ1kOgC4knQBLiVFCidwCgo/Zrj6jpJ4uF9i4yUuDPuYIJuEg9oCvQj0pvPrPRLaiBuiB5Xq1U2UTGadDbQ+NAPOuZukUEcJ915rhUm+SgT/C1LWU7/AJJpVbGZX0g9k6gifM/Gi2EkXK8s7uiP9ImpxiQmxhY+8smqc2v6QBWNmND/ADGY8OjPgJprhbQdJPHSpHcWmf3aI61n9KUYppvpFKOzNPrSUpdwHYfaKNEoPbeg8V0yZ8v1NRYzbrcwAkdiTQ3/AGgk6q8LVaxy5oCRBCT+7McTAHlNR4zEnTMQPv0FjH2p3n81DLeQBZNvnjNbrH3EPUkTOc+PwNE4V5I4k9hIpcHtNI9lseAqwwuNcVYAJ7h605X3GK3tFWgbn8J95NSOPPqHsx+GPMJp5wzpF1+Z9L01TKo3EjjP6VhsBBLnYer9SKgfU9x76L/aXE/VT3Zfeaa9iXSLgDw91Wr+gFcULPtK8E++aXL/AMxfialKlbyfzCkK1cT4pq7YB+HwoB4n0+eNTqcyi8cLaX3H566jS1BvF4IFibDf29IQL6ddQuuKBlKSqTfhF9d9J7lEGdSXIMAcT3C0m51qZPRGaTY3nXdpbXq6hpTsXgAs5lEpMQqNYF8vZeJ/tUwUC2YEBNoPUBxPV60m0IE/a0woJgmIKZSCmYI61TYcKezBKVKBzGJjTqnLr4mIqp2PglKfUoFUJmCkHLwAChMEcd16usXKAMyVISIukAgduluMXFVJKLpDB9o4kTlVcK4Dd1kXI8qseSmFQ8sqCBkbIUn2ozT0QZPSuCSN4SoVS7SIcShULKbzETJ6lEGLHpbq3HJHDBrDJCiQVAuwctkE9EgpspOUJMiYKyJrr6LAsk1fbkzyz0wbBdotBTkXJFipRlRJBMFR4JkxpK0xQrrfz2VaNMkmSLlOY8ZcMlJ60pSgUPjU5UKMaD0BV/THfX00KSs8idtpEOBwYLK3T3feWqEn8iSarX8GkuMpM5VOJQrd0Va+lat5kIw6ER9cjubQAP8AWaptsMwgKAgpU2Z/EAT4Gm/+t/nBKf8AyL85G7KQlxDmAfuOmG51hJJKR1pIzp7DwFebbW2evDurZXqk67lA3Ch1EV6dyiwq/wBpKmkqzKUHG8okkqAWIA1vfuobljspONwicYgBLjQPOC9kj94k2nomVC3sk8a5M0e6O7BPszzNlBJCREkwL++r7ktyjOAccVzKXFkZOkYyQqVRY62HdVOlqDZWnDWx3AgHyNFbRZC8ikCSQM9oGaAVKv1kj8PXWHOzOi6Ctr7dD7ynuaCVqIMWIEADSOlpv91DsOXC8osoEgbxoYHaR40xrAABRUCTEJEwAeJjXsFXHJtjDJfBxRVzISUqSkKJXmEXIIKY1twApp0iWrCA6BlWhKDBkAzBEb8sHzrc7HdedaBwhAUR/iYZ8hYKRMc2tYzFKuCjvF41xy8QyELabdVlhC0FSTZxKRmEAaGXAPwddWjzjgZRimXCFoUkz/LfjIVWLb4Y1sXjGJQ9mbKSw6iAW13CTuyKVdI4JV0dAC3NYrlMcVh15XAnJmgLhQE6xrYxeDeLiQQT6fh0NbSaDoyoxLYyk6i4uhY+s0ry1FwRWexKnGczWJaLmGnLmMKUzlvkWTAUkTIkgwQpJBg1xZMMHK2jZGX2fnXBCieuCfCU++p3XYstZHckU/a2zFsjnmXVOYcjMCCDlTvNgJSLSbFP1gOipWaxWLSriVcZBHrXBPp5KW4FxiubVYkkdo+HvqrewpJgCeF1e6n7K2YVkEyeokx5VqcPs1tESyCfx++oc1j2W4GWwuw1k9IBP5p8zFEPbCbH/EM93xFaJ1SU/wDCI8BQ7mOm3Mg9uvpUe/kbsKM0NhpUbuLgcQryvVwxshlI/eKI7DHmqpcQ6CJLaU91/QVWu4xu6bnuJ99aa5zAnxOHaSLOK7o+BqscWZkEnu/Spy2oiyV90/Cq97CLBnpjvNaQS7sCVvFOTGUx2fFNWWFWDqFeQ/pqow6VzdLhHzwNWqEf8pyPxfGnkoZaNpZjpJ8Z+FP/AMAaBI/CfhVK4N2QjtHxNRJYXM5gkdX96x9u+4i3xLgiEny/Sqx1K5sD4j40inlD6/kn40O5tAg+1/pFVGDXAG5xHJs3IK9ItB75SQRuPs7tJJoROxXARKkAXlOVRuZiBoPCtyGknQwaYttXaOuup9P4Z0aV4POtp4F1IzJCVm0CSLWmx1uPIVFg0u6rSVDXeZNwddd/6V6E9hkKEKb8BFQnZjZiJFyTI1kzutoYmN1ZPDNKqTFoMM48kLskJVYjcYBJmMpuY10orFZzu1HtEJVv6rRrpe1aZ/YgnNE2IgTEHd47qlbZCUZS2ewA8IiTc1hJOPKGsZlNibDbdfbZJCgpYzWg5B0lCRe6UkdVerrwDDqAlSGlp0AAEARECNLWtFrVmNhYJLeJS+QbJMpA+0Mswbze96udu7Pad5tUWKgbSCFCIPRIi1uuvT6OVQb+pjkhvQQ7yaaMlKnEkmTCgqTAH/ECjoBvoJ/YLTQLj687KbqAGUiI6SlZoyi8xGvbRrT7iPrFQ8fX3VG/tp4PNpGHKm1QFLSpIyTOYqSqDaxsbibE12rNKqsyeGN3QTs/lBsxQARiMMNbFSAevUyayfLQYdSMSGXEE5ArKlSYAgKJAG6x6ql5T7Iw7zobbwrJXGYkNIClST9aLgdupvpV/szYaA1zT+Ew1kgAtoQAQLgLRlAkSbp3k6VUW4LVd2RJKb01VGO2XyiDgLrSSFsJDKipMiCISoQdbEXjWKg5MbWCcUpCzKXz0pAA50mxiw6UlMRrlrWK5FYWSWw4wo+1zauirtSsKHhFWOy+TuHYOZDYK/tr6S+4myfwgCrWf4tSW5DwNSTi9jzHbHJV1rEqbYwLjiRC0LRlCQlROUFSoAUII1kwDvqNvkfjj/k0o++81/QTXtBbntGhGt9fQWPAVym+IkdXwPz1Vz62dGhHjyOQmOP1MKO11w+jZohv6PsWfaXhU9hdV6pTXqoYH1T3cO0G48qTIRqPCjWw0I8xH0cvHXEtDsaUf6xVhgORD7SVIGMbKFapOFB81OG3VW/CaXJScmxqKMhs/k08yorbxSUqIglOHSJHWCsjy41LjNhPOqKl4s9JISoBlrKsCYzAzPtHy4VqiimlupHRhtk8jFYYFLWLXlNylSARmFgodIFKotII1pMdyPMAtFsmLoypQCeKNQmfszE6QIA26mqiU1Wc8UZqmM8nxGELSsji1tq3JUgeIgQR1iqvaONWm3OgjjkivY9oYBt9BbeSFDcTqOwi47RevIeWXJNzBnnWypxkqgzBU2SYE9EykmADxIB3E8b6PS7TtCoq1kr9rOTxSD7008rUj7f4gP0oRraQAhQUPwq/6KAx+MSrRxX81QsTbqgou148EQUIPbHxpBjEJHR5tP4fgTWRUozOdXz30UxtBQtm8p9a0fTUtgovjtkgWxKR1ZFVV4nbTpP/AIjyPvNc4vOLhHgP+qhXsKAJCQfzfGnDHBc/6EWGE22vQuZuu49CKORjs3A9hc9xqjaxykixSKscDtJwj6h/DPqKMmJcpFBeLbJFk+TnvoIsWun+RXwo1t4qPSED+EAD0olbYy2WseNZJuOwjOYlKRaP5fiKh/Zgd4/Kault/wDNXQyvvny/6a2jMR7QhRFTofqO1NKK3OkMSoGlLXdQiVVO29QM5TR3GuC1cfGp0qB404ppAZzlltF1nCOLZs6ciEkagrcQnQ2mDR/JDaqsRhRzhSp1ByOFOhUE+0IA1BBtaZA0ofldh0/sqydAppR7nmyR5VW8jMURiVpJu82rN/7mHWAe/K6En7laQSoznybUefrTiOIqPPuNTJ8aZIiQRpTkPkb4+eFKE8KRSeIoAPYczJnup4FZ7aG2GsGjnHnktpJiVScx4BIBJPYDR2wtus4lGdpxDiZjMk7/ALKhqk3FjGtaKRDiG7Sxa22lrQjnFJE5ZIkA9K4BuBJ03VT7I5YJfCSnDPGf/LyOZfa9qFBST0SYIki4EEVoiN9Y3a7OzG31hbbrLoCFFxkPgwuSkgsydQoWGqTwqqT7Eu13L9HKXBqjM4UEzBWh1GljCykDWxg9VFs7SYV7GIZc6g43m8J+FY1GAweZLjW2H2VAGOectEZSCjEAAi8XHCi1cm33UZWsXg3hkyBRZRnABJBStlXRInWOqppDtmxQ2FXT38e8V3N1gkcgcSkGVhJmQQSqIvADgmN11d9Duck9pJJyYsRNugkW3TCqKXkLfg9EyU0orzlXJrav/qf5o/qqJfJnax/zR8QfVVPSvP59xan4Ntyi2y3hGedcBIzBISMskmSYzECyQpRJOiTSbP22w83zqHU5d8lIjtvHeCR11gV8g8c6oDEYlK256QKU6ax0bkSBIkTESNasdofRuhQHNYl1s2zadLd9QAWFhIJvrxTpIabNDjuU+DbBKsS2Y1yHnD4N5jWQ5R/SDhltqabQV5wUZnOigBQIJKRKzAvBCe2pmvouY1exDrngnzM1dbI5P7OZXlaQyXNbqC123wSdOIFZ7lHlOK2QkISrMtJUlKilQgpzJCoMjgaosVswTZYPhXpe08OrEYnE5nMq0OQEJP8Aw8oDaz96FHvjdVC9steaCvMOBk+6uBZNEmrNNGxkW2SkQUg/hFqatgKFkDuAFb0YBsjpIPp7vfVTjNmtz0U24SQfI1Uc9sHAx7WFG9RHVI+NTKwoI9s1ontnMfaWOz5NVW0sA2lJUnpdsz6CtVk1MhxKRxEH4ilbdg6x31MpSY3+f60MESda2W63JLjC7SdA6Kx3hPwqdG0cQTBUk9yaDw+zlRZaOImR5xRScAvcUHsWn3msJKH0K3ExPOkbh2JI91V/7M59vzNHPNrAuD4AihCr5gU47IGj31DJUYAk8Bqac4ypJhSSk6wd4piFREEzuOhBrRMYhOKRzblnU3SqPa4kdfEd46taNmzOxSUVi8IptWVVuHAjiDvFQQaQzkLqdDh41Bl40ooAG5RALwzoPBJ8FpOndWIwm0ktv4Z7QArQqY0CEoUsnrjN1WG6t7i2s6FINgpJTPCRE++vJuUOMS2sJUMik55RqQpZExxTCbHeBO+rhxRnNb2eyoxKTvlOk8D9k9frrvqZIi4Nq8O2TylxbKw40l11sJ6acqiIH8UG2hvIFehcneXWGxEJzc04fqq39nHuJ7BTaFybVt3jT3VWoRt0ETaOI0/Q9VPUbUCPKeXTX7XtQMrWUsMJQknW6gFkJAuVKKkptrAFTbExyMHiEhLCmZAGUgguJ4LkDNpZREgjUgkEp9OXHYxw6hYjtLacp8C4O/qoLGgvsFJ9tILjZ3yBJSO0AiOITwqkSe04HEhaAoGQQCDxBEg+BFZjlzsV10IxGGBL7MjIDHOtK9pvUXBAUkH+LWYLPo52nzuGTJuPfJ9c47hWtNFhR4uvlE9ziE4oc0gB1IQ60pASkpVbppSYuZTfNYWNxNtzaODeczNJZfCW1KWtQUpWfOAklZKT7KkzEgK47vaEqtG7huoDFbEwjn7zC4dc71NNk+MTVa2ToR4e5tlbYSlBeaWoGFN4jENpBzESGwdABxF7V7N9H+IdcwCHMQoqUpS8ilElRbBgZibm4VB3iKaOSezwrMMFh5+4I706Hwq1ee0HcANwG4DQChytAo0zIfSBy5OCWhpltC3FJzkrJypSSQNNSYVv3ddYH/edtN2zSGsxmyGVKMWvdR3nhQv0j4tZ2jiASRl5pI005ltXqpR76vfoadP7U/nX7LCQJIsOdKjfhKp76FQ9yvG1eUDx6KcSBaYYQgdcFSB2a0//AGe5QPE5lvpG7NiUoA7Q2qfKvWcZygwjX7zFMI+86gHwmgDy2wR/duqePBlp5zzQkjzo2Gecf7qdoPEc8+yPvOOuHzT76yOHJwmMA1OHfAzptPNLCFRvKSEERwMV7mrlWTHN4LFHrcDTI/8AlWFfy15hiNlsoxKnsXiWEJLzj3MtkuLUFOFzITAAF4JAO/jUt+Ao3YwKBiXVZRmWEhRvKsnRT4SfLgIkc2ej7F+IrM7C28cVjFuJCi2ErQkERrlJVxJVG/QCIF50zuOKTwrx+qv3GdmNfEgThQLQRUa9ngzCgD1j4VYIxs70n1risHVNc9suimd2Mk6pQTxiq/Gck2lCdD1ZffNaZeHSdDUTmFPaKpZGiXFPseabU5MBIMKIjhJ+FZVeAKT9Ydot5V7U5slCvaSfE1H/ALO4f7Pv9a6IdU1yZPFZ5tgy5lEFHh7qsG1mOm2hXiPWtt/s8xuB7Bb0IoF7YrYPRUtJ6yT5ke+k80WDxtGVfbCjZtI7CPdFCKw6fsp7/wC9X+0Nhk/Wnrge6qdeyHAYk/zfGqjJeTNxZ6qBU6FEaEgi/wCoNBpVU6T4+td5oaXB4pGITzbg6WoIiSftJ/i4jfVTjsGppUGCDooaH4Hq/vQiVEXGuvz11bq21mbKVozHf19fUqnyTVcFMU0mS9PSofOtcTUliFJqFTV7gUQBSgigCAJrP7e5GYbEycvNuH66Iuf4k6K7bHrrSkUlCdcBV8nmpTtLZpkEvsjeMxhPX9ZA7cya0uweX2HfhKzzazxgSer6qu4g9VaWszt/kRhsTKgOacP1kAQT/EjQ9tj11aknyQ4eALlICh95aDZzmF23w2pEjsKJqENFBbdKVDOUOJBIKYUSSBb2dRG7jQ2H2U/hUONYhQcBgtLkkZEhSVJvcEc4FAG3AmDAuExziwEqMhOUJBg5RmJtOmguL91Wqoyd2aD6NsTzbzrO4LdSO1KpHlzlenFYFybb+qvE9gY3m8Y45oP2oz1JWpaFH8qjXrePQpxh1CSMy23EiTHSUggX3XOu6gDzzaHKhx545FkG5/xFrQhCZhKAhBF4iVEmSTFiAC8ByofQsc5zKkiJCXnASOF3D6VQvYJ5nGqeLaR0lkIUUoIzJISYWpAi+5UiNOM21NiuYtYWppaSEhCVNw6SASRnCQc6rm4WLQN0m+xPDLvaPLxxBUvIoImwDiLSbDptqnxqDB/Sb0v8RlZTBuktlQMWNsoPCLazO41quQuI5qbwDYlC03g2UFC2u4msrjdlPIc5tSCVQSAmFTA3ZUmkM1+1uV2z8QoKdwC3FRAUqEmLwCpC5IuddJqod5RYIGEbKw/41ZvJaT61U4Xk9ilkZcK8estKA8SE1YYTkHj1f5coHFa0DyClelGwDxyyWj9zhcIz9xkA/mTFC4nlpjlz/wB4UBwSEx5Cat2/o6eSJexGGa68ylHyCPWmq5N7Obu/tIuRqGkp+CzRsBksXtF1z23XFdSlKI/KTQjSCpQQkFStyUgk9wF62bm1Nis+xh3HzxcWSk/hJ/pqNf0iqSnLhcOywn+FP9h5UAWn0e7LW2HHHGlIPsJK0lJMwpcAifqok1sHG8w1FBcmdoKew7by1lalpBMkdEiykgDS4PzFXHROorgzYVOTZ145aY0VS8EeHhSobI3mrYtDj41Epnq8D7jXNLp5I1U4giSamQ6aUt/JHvFNLZ3GfOsnja5L2Y/nuNIXEHUkd0+lQqkbqilJ6qnSKkFhlJ0Uk+XlT04WP0NV/M8D4H3UwurTvPfS0i0lm7hQoXTPakGgV7NRwjvIpEbSUNaf/wBrjiaKZLSJAqpkrkUKk6fPz+tTIXNeyYEwWakSbUOF3qZNxQBIEzpr61GlXGxpwNI6mTIMK3Hj1GkMcTXUwKndBGopwoAcKaeqlmloAaDxpQa43pmlAFbymwinGSUCVoIWkfagEKR+JJUO0isYy4yBzqFZiBKW7ZpAslSdQJgE6RpMivR81ZzafJRKlqWy4tlS5zZbpJO/LYg/dUPGri62IlG9zApGRBSoypSjM7z7N/xBVWCfpBew8II51P1TnIUBwNjNoPfVj/u5KlS5i1EbghATA4CVHd1Ue19HeCCYUlxR+0pZkdmWB4iq1ojQwDCfS2QILTgHAKBHnFHt/Srhz7bC+9to+poJ76M2fqPup+8EK9AmgnPoxX9XEoPa2oeijT1RFokaVP0tYUJyhteWZyhpuJjWJigcX9LbKQeYw6gojUoaTPeCTVAr6NMRudYPe4P6DSt/RliN7rIHUXD5FIouPkWmXgF2l9J+NcPQJbTwBBP5oFUeJ5WY1z2n3OzOqPCa2DP0YH6+JHYlv3lXuqzwv0cYVPtreX+JIH8qZ86NcStEjypeKdUSSs3pjbC3DlGZZ4CVHwFe34XkfgkaYZB+/K//ALCatmsIlAhKQkcEgAeAqfcXZDWJnieB5G4xyIYUkHeuEeSoPlWk2b9HC5BeeSkb0tgknsUqAPA16WGq7m6n3GUsaAtmYBDDaWmxCUiBxuZJJ3kkk99GhVdkpsGoLJEuU8LoYjqps9dOgsMz00kbxQ0mu5ylpCycgcaicZB3Cm89Tg6Kh40+xWpkBYjSfXyqNSOsUbIppqHgiVrYAWOqoF4S9WKgOEfPVTD970rJ4GPWnyRNr3d3z5+FSBV5+ev499RoF7/PHzFdN4NdxgE5oN9KnRr6UG2SRG8UQ2uaQycKpVJqLN+tOzeFIZxvY2I0NSIXeCIV60wGlWjMOsUgJVJplNZd+qdR59nz+spHnTAjroqRQ+eNJFAEZTXA08imxQAtLTCK4KoEPy0oTSClCqBjubrgmumnBVACZK7JTkqp9qVBZDlrpqUilAFFBZFANIW6mUzwqPSgdkSkmmURmBpqk0CB1JqIiiFJqNSKYA6kmmEGiSKaaYgYikqZSajKKAEDhpefpigajVQARztNK+yhSqk5yigsdn39h+fCpFGY7v0NdXUxD2zBn56xRMcO6urqBjkqm+/fTgukrqQEqVU7rFdXUhiLSFC9uB4fpTG3iDlXr5H9a6upAET3ikjwrq6gBFGK6a6upgNJiuKQa6uoAYQR83p4VXV1ACinTXV1AhQacDS11ADgqupK6gBQoinc5OtdXUh8ka0ioynga6uoAQq40hikrqBjSKYoGkrqYhihUZrq6gCMn5/WmKFdXUxEak1GU0ldTA//2Q==" alt="Hatchback" class="car-image">
                    <h3 class="car-name">Hatchback</h3>
                    <p class="car-description">Compact, efficient, and easy to park – a perfect choice for city driving.</p>
                    <p class="car-price">$30/day</p>
                    <button class="car-button">Book Now</button>
                </div>
            </div>
        </div>
    </section>

</body>
</html>
