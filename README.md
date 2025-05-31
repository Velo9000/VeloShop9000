<!DOCTYPE html>
<html lang="nl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fietsonderdelen Verkoop</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Gebruik het Inter lettertype zoals standaard in Tailwind */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6; /* Lichte grijze achtergrond */
        }
        .product-card {
            transition: all 0.3s ease-in-out;
            cursor: pointer;
        }
        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
        .details {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.5s ease-out, padding 0.5s ease-out;
            padding-top: 0;
            padding-bottom: 0;
        }
        .details.open {
            max-height: 500px; /* Ruime waarde voor de inhoud */
            padding-top: 1rem; /* 16px */
            padding-bottom: 1rem; /* 16px */
        }
        /* Stijl voor de "Meer info" knop */
        .info-button {
            transition: background-color 0.3s;
        }
    </style>
</head>
<body class="bg-gray-100">

    <header class="bg-white shadow-md sticky top-0 z-50">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <div class="flex items-center">
                    <svg class="h-8 w-8 text-blue-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
                    </svg>
                    <span class="ml-2 text-xl font-semibold text-gray-800">FietsFix Onderdelen</span>
                </div>
                </div>
        </div>
    </header>

    <main class="container mx-auto px-4 sm:px-6 lg:px-8 py-8">
        <h1 class="text-3xl font-bold text-gray-900 mb-8 text-center">Onze Fietsonderdelen</h1>

        <div id="productGrid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
            </div>
    </main>

    <footer class="bg-gray-800 text-white py-8 mt-12">
        <div class="container mx-auto px-4 text-center">
            <p>&copy; 2024 FietsFix Onderdelen. Alle rechten voorbehouden.</p>
        </div>
    </footer>

    <template id="productCardTemplate">
        <div class="product-card bg-white rounded-lg shadow-lg overflow-hidden flex flex-col">
            <img src="" alt="Product Afbeelding" class="product-image w-full h-48 object-cover">
            <div class="p-4 flex flex-col flex-grow">
                <h3 class="product-name text-lg font-semibold text-gray-800 mb-2">Productnaam</h3>
                <p class="product-price text-xl font-bold text-blue-600 mb-3">€0.00</p>
                <div class="details mt-2 border-t border-gray-200">
                    <p class="text-sm text-gray-600 mt-2"><strong>Maat:</strong> <span class="product-size">N/A</span></p>
                    <p class="text-sm text-gray-600"><strong>Kleur:</strong> <span class="product-color">N/A</span></p>
                    <p class="text-sm text-gray-600"><strong>Materiaal:</strong> <span class="product-material">N/A</span></p>
                    <p class="text-sm text-gray-700 mt-2 product-description">Gedetailleerde beschrijving hier...</p>
                </div>
            </div>
            <button class="info-button w-full bg-blue-500 hover:bg-blue-600 text-white font-semibold py-2 px-4 mt-auto">
                Meer Info
            </button>
        </div>
    </template>

    <script>
        const products = [
            {
                id: 1,
                name: "Racefiets Zadel Pro",
                price: "49.99",
                image: "https://placehold.co/400x300/EBF4FF/3B82F6?text=Racefiets+Zadel",
                size: "270mm x 140mm",
                color: "Zwart",
                material: "Carbon Composiet",
                description: "Lichtgewicht en ergonomisch zadel voor de prestatiegerichte racefietser."
            },
            {
                id: 2,
                name: "Mountainbike Band MaxGrip",
                price: "34.50",
                image: "https://placehold.co/400x300/E0F2F7/0EA5E9?text=MTB+Band",
                size: "29 inch x 2.35",
                color: "Zwart met blauwe accenten",
                material: "Dual Compound Rubber",
                description: "Robuuste band met uitstekende grip voor technisch terrein en modderige paden."
            },
            {
                id: 3,
                name: "Stadsfiets Pedalen Comfort",
                price: "22.00",
                image: "https://placehold.co/400x300/FEF3C7/F59E0B?text=Stadsfiets+Pedalen",
                size: "Standaard 9/16 inch",
                color: "Zilver/Zwart",
                material: "Aluminium met rubberen anti-slip",
                description: "Comfortabele en duurzame pedalen, perfect voor dagelijks gebruik in de stad."
            },
            {
                id: 4,
                name: "Ketting Shimano 10-speed",
                price: "28.75",
                image: "https://placehold.co/400x300/F3E8FF/8B5CF6?text=Fietsketting",
                size: "116 schakels",
                color: "Zilver",
                material: "Gehard Staal",
                description: "Hoogwaardige en slijtvaste ketting voor 10-speed aandrijfsystemen."
            },
            {
                id: 5,
                name: "LED Koplamp SuperBright",
                price: "19.95",
                image: "https://placehold.co/400x300/D1FAE5/10B981?text=LED+Koplamp",
                size: "Compact",
                color: "Zwart",
                material: "Aluminium behuizing",
                description: "Krachtige USB-oplaadbare LED koplamp voor uitstekende zichtbaarheid."
            },
            {
                id: 6,
                name: "Handvatten Ergonomisch Gel",
                price: "15.50",
                image: "https://placehold.co/400x300/FEE2E2/EF4444?text=Handvatten",
                size: "130mm lengte",
                color: "Zwart/Grijs",
                material: "Gel en rubber",
                description: "Ergonomische handvatten met gelvulling voor maximaal comfort tijdens lange ritten."
            },
             {
                id: 7,
                name: "Fietspomp Compact Air",
                price: "25.00",
                image: "https://placehold.co/400x300/DBEAFE/3B82F6?text=Fietspomp",
                size: "25cm",
                color: "Zilver",
                material: "Aluminium",
                description: "Compacte en lichtgewicht fietspomp, makkelijk mee te nemen."
            },
            {
                id: 8,
                name: "Bidonhouder Lichtgewicht",
                price: "9.99",
                image: "https://placehold.co/400x300/E0E7FF/4F46E5?text=Bidonhouder",
                size: "Standaard",
                color: "Mat Zwart",
                material: "Kunststof",
                description: "Sterke en lichte bidonhouder, houdt je bidon stevig vast."
            }
        ];

        const productGrid = document.getElementById('productGrid');
        const template = document.getElementById('productCardTemplate');

        products.forEach(product => {
            const cardClone = template.content.cloneNode(true); // Kloon de template content

            // Vul de productinformatie in
            cardClone.querySelector('.product-image').src = product.image;
            cardClone.querySelector('.product-image').alt = `Afbeelding van ${product.name}`;
            cardClone.querySelector('.product-name').textContent = product.name;
            cardClone.querySelector('.product-price').textContent = `€${product.price}`;
            
            const detailsSection = cardClone.querySelector('.details');
            detailsSection.querySelector('.product-size').textContent = product.size;
            detailsSection.querySelector('.product-color').textContent = product.color;
            detailsSection.querySelector('.product-material').textContent = product.material;
            detailsSection.querySelector('.product-description').textContent = product.description;

            const infoButton = cardClone.querySelector('.info-button');

            // Event listener voor de knop om details te tonen/verbergen
            infoButton.addEventListener('click', (event) => {
                event.stopPropagation(); // Voorkom dat de card click ook afgaat
                const isOpen = detailsSection.classList.toggle('open');
                infoButton.textContent = isOpen ? 'Minder Info' : 'Meer Info';
            });
            
            // Event listener voor de hele kaart (optioneel, als je wilt dat klikken op de kaart ook werkt)
            // cardClone.querySelector('.product-card').addEventListener('click', () => {
            //     const isOpen = detailsSection.classList.toggle('open');
            //     infoButton.textContent = isOpen ? 'Minder Info' : 'Meer Info';
            // });


            productGrid.appendChild(cardClone);
        });
    </script>
</body>
</html>
