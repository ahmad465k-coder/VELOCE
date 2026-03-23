<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VELOCE Cafe - Breakfast Menu</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;700;800&family=Open+Sans:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Open Sans', sans-serif;
            background: linear-gradient(135deg, #0d0d0d 0%, #1a1a1a 50%, #0f0f0f 100%);
            min-height: 100vh;
            padding: 40px 20px;
            color: #f5f5f5;
        }

        .menu-container {
            max-width: 1000px;
            margin: 0 auto;
            background: rgba(20, 20, 20, 0.95);
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.08);
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.8);
            overflow: hidden;
            position: relative;
        }

        .menu-container::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, #ED3924, #ff6347, #ED3924);
            background-size: 200% 100%;
            animation: gradientShift 3s ease infinite;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .header {
            text-align: center;
            padding: 50px 40px 30px;
            position: relative;
            background: linear-gradient(180deg, rgba(237,57,36,0.1) 0%, transparent 100%);
        }

        .brand-name {
            font-family: 'Montserrat', sans-serif;
            font-size: 4rem;
            font-weight: 800;
            letter-spacing: 12px;
            text-transform: uppercase;
            background: linear-gradient(135deg, #ffffff 0%, #e0e0e0 50%, #ffffff 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 5px;
            position: relative;
            display: inline-block;
        }

        .brand-accent {
            color: #ED3924;
            font-family: 'Montserrat', sans-serif;
            font-size: 1.2rem;
            font-weight: 300;
            letter-spacing: 8px;
            text-transform: uppercase;
            margin-top: 10px;
        }

        .menu-label {
            display: inline-block;
            margin-top: 20px;
            padding: 8px 30px;
            background: rgba(237, 57, 36, 0.15);
            border: 1px solid rgba(237, 57, 36, 0.4);
            border-radius: 30px;
            font-family: 'Montserrat', sans-serif;
            font-size: 0.9rem;
            letter-spacing: 4px;
            color: #ED3924;
            font-weight: 600;
        }

        .menu-content {
            padding: 0 40px 50px;
        }

        .category {
            margin-bottom: 50px;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 0.8s forwards;
        }

        .category:nth-child(1) { animation-delay: 0.2s; }
        .category:nth-child(2) { animation-delay: 0.4s; }
        .category:nth-child(3) { animation-delay: 0.6s; }
        .category:nth-child(4) { animation-delay: 0.8s; }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .category-title {
            font-family: 'Montserrat', sans-serif;
            font-size: 1.4rem;
            font-weight: 700;
            color: #ED3924;
            margin-bottom: 25px;
            padding-bottom: 12px;
            border-bottom: 2px solid rgba(237, 57, 36, 0.3);
            text-transform: uppercase;
            letter-spacing: 3px;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .category-title::before {
            content: '';
            width: 8px;
            height: 8px;
            background: #ED3924;
            border-radius: 50%;
            box-shadow: 0 0 10px rgba(237, 57, 36, 0.6);
        }

        .items-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
        }

        .menu-item {
            display: flex;
            flex-direction: column;
            background: rgba(255, 255, 255, 0.03);
            border-radius: 16px;
            border: 1px solid rgba(255, 255, 255, 0.06);
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            cursor: pointer;
            position: relative;
        }

        .menu-item:hover {
            transform: translateY(-8px);
            background: rgba(255, 255, 255, 0.08);
            border-color: rgba(237, 57, 36, 0.4);
            box-shadow: 0 15px 40px rgba(237, 57, 36, 0.15);
        }

        .item-image {
            width: 100%;
            height: 180px;
            object-fit: cover;
            border-bottom: 3px solid rgba(237, 57, 36, 0.3);
            transition: transform 0.4s ease;
        }

        .menu-item:hover .item-image {
            transform: scale(1.05);
        }

        .item-content {
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex: 1;
        }

        .item-info {
            flex: 1;
        }

        .item-name {
            font-family: 'Montserrat', sans-serif;
            font-size: 1.1rem;
            color: #ffffff;
            font-weight: 600;
            letter-spacing: 0.5px;
            line-height: 1.3;
        }

        .item-price {
            font-family: 'Montserrat', sans-serif;
            font-size: 1.1rem;
            font-weight: 700;
            color: #ED3924;
            white-space: nowrap;
            margin-left: 15px;
            text-align: right;
        }

        .price-note {
            display: block;
            font-size: 0.75rem;
            color: rgba(237, 57, 36, 0.8);
            font-weight: 400;
            text-transform: lowercase;
            margin-top: 2px;
        }

        .highlight {
            background: linear-gradient(135deg, rgba(237, 57, 36, 0.15) 0%, rgba(237, 57, 36, 0.05) 100%);
            border-color: rgba(237, 57, 36, 0.4);
        }

        .highlight .item-name {
            color: #fff;
        }

        .footer {
            text-align: center;
            padding: 30px;
            background: rgba(0, 0, 0, 0.3);
            border-top: 1px solid rgba(255, 255, 255, 0.05);
        }

        .footer-brand {
            font-family: 'Montserrat', sans-serif;
            font-size: 1.5rem;
            font-weight: 700;
            letter-spacing: 4px;
            color: rgba(255, 255, 255, 0.3);
            text-transform: uppercase;
        }

        @media (max-width: 768px) {
            .brand-name {
                font-size: 2.5rem;
                letter-spacing: 6px;
            }
            
            .menu-content {
                padding: 0 20px 40px;
            }
            
            .items-grid {
                grid-template-columns: 1fr;
            }
            
            .item-image {
                height: 200px;
            }
            
            .category-title {
                font-size: 1.2rem;
            }
        }

        .image-placeholder {
            width: 100%;
            height: 180px;
            background: linear-gradient(135deg, rgba(237,57,36,0.2) 0%, rgba(237,57,36,0.05) 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            color: #ED3924;
            font-size: 3rem;
            border-bottom: 3px solid rgba(237, 57, 36, 0.3);
        }
    </style>
</head>
<body>
    <div class="menu-container">
        <header class="header">
            <h1 class="brand-name">VELOCE</h1>
            <div class="brand-accent">cafe</div>
            <div class="menu-label">Breakfast Menu</div>
        </header>

        <div class="menu-content">
            <!-- Middle Eastern / Kurdish Plates -->
            <div class="category">
                <h2 class="category-title">Middle Eastern / Kurdish Plates</h2>
                <div class="items-grid">
                    <div class="menu-item highlight">
                        <div class="image-placeholder">🍳</div>
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Kurdish Breakfast Mix</div>
                            </div>
                            <div class="item-price">
                                10,000 IQD
                                <span class="price-note">per person</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Egg Plates -->
            <div class="category">
                <h2 class="category-title">Egg Plates</h2>
                <div class="items-grid">
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/www.recipetineats.com/2e21a929c4919cf9035801ff0d66b27ef978788f.jpg" alt="Classic Omelette" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Classic Omelette</div>
                            </div>
                            <div class="item-price">4,500 IQD</div>
                        </div>
                    </div>
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/www.mygorgeousrecipes.com/234387d7428b6200dad2b96d53c57c98ac904bd2.jpg" alt="Vegetable Omelette" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Vegetable Omelette</div>
                            </div>
                            <div class="item-price">4,000 IQD</div>
                        </div>
                    </div>
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/www.allrecipes.com/f2b58fddc90b536432f0d4327c5f5af4cff85242.jpg" alt="Scrambled Eggs with Cheese" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Scrambled Eggs with Cheese</div>
                            </div>
                            <div class="item-price">4,000 IQD</div>
                        </div>
                    </div>
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/littlehousebigalaska.com/47710ed9a3cddbe1cec21b615d5972c6ea2a69fc.jpg" alt="Fried Eggs with Sausage" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Fried Eggs with Sausage</div>
                            </div>
                            <div class="item-price">5,000 IQD</div>
                        </div>
                    </div>
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/www.themediterraneandish.com/4e2d67cfaa38e782493d193803954dfe26ab531c.jpg" alt="Shakshuka" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Shakshuka</div>
                            </div>
                            <div class="item-price">4,500 IQD</div>
                        </div>
                    </div>
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/www.twopeasandtheirpod.com/bb29009f5ef8ec9c47d2e85c105accaf3db02dec.jpg" alt="Egg Sandwich Plate" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Egg Sandwich Plate</div>
                            </div>
                            <div class="item-price">4,000 IQD</div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Healthy Protein Plates -->
            <div class="category">
                <h2 class="category-title">Healthy Protein Plates</h2>
                <div class="items-grid">
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/tastesbetterfromscratch.com/b0670eb6b8412e9206b215bd3d0acfde6d237fe1.jpg" alt="Fresh Fruit Bowl" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Fresh Fruit Bowl</div>
                            </div>
                            <div class="item-price">3,500 IQD</div>
                        </div>
                    </div>
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/www.halfbakedharvest.com/10272aa07794ee66c1165f091eb88285f6480504.jpg" alt="Yogurt & Granola" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Yogurt & Granola</div>
                            </div>
                            <div class="item-price">4,000 IQD</div>
                        </div>
                    </div>
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/wholefoodsoulfoodkitchen.com/770507828d21d225e2314e83d5b91be598789f7c.jpg" alt="Oatmeal with Milk & Honey" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Oatmeal with Milk & Honey</div>
                            </div>
                            <div class="item-price">3,500 IQD</div>
                        </div>
                    </div>
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/www.aberdeenskitchen.com/340320fc8d76f226500ed14d7d92dd97bde99f8c.jpg" alt="Avocado Toast with Poached Eggs" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Avocado Toast with Poached Eggs</div>
                            </div>
                            <div class="item-price">6,000 IQD</div>
                        </div>
                    </div>
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/data.thefeedfeed.com/945ca1f40e3694211ce4dffa7bc1e2e1595097d3.jpg" alt="Grilled Chicken Breakfast" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Grilled Chicken Breakfast</div>
                            </div>
                            <div class="item-price">6,500 IQD</div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Bakery Plates -->
            <div class="category">
                <h2 class="category-title">Bakery Plates</h2>
                <div class="items-grid">
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/bakingwithbutter.com/cc9255c888aa0bf9a78ff213eac507a901dad05d.jpg" alt="Butter Croissant" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Butter Croissant</div>
                            </div>
                            <div class="item-price">2,500 IQD</div>
                        </div>
                    </div>
                    
                    <div class="menu-item">
                        <img src="https://kimi-web-img.moonshot.cn/img/urbanfarmandkitchen.com/4069cfeb311ac6020ac3cec39ea625ab51249c6c.jpg" alt="Cheese Manaqish" class="item-image">
                        <div class="item-content">
                            <div class="item-info">
                                <div class="item-name">Cheese Manaqish</div>
                            </div>
                            <div class="item-price">2,500 IQD</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <footer class="footer">
            <div class="footer-brand">VELOCE </div>
            
        </footer>
    </div>

    <script>
        document.querySelectorAll('.menu-item').forEach(item => {
            item.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-8px) scale(1.02)';
            });
            
            item.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0) scale(1)';
            });
        });

        document.querySelectorAll('.menu-item').forEach(item => {
            item.addEventListener('click', function() {
                this.style.transform = 'scale(0.98)';
                setTimeout(() => {
                    this.style.transform = 'scale(1)';
                }, 150);
            });
        });
    </script>
</body>
</html>
