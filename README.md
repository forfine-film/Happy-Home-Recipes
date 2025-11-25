
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Home Recipes - สร้างความสุขในทุกมื้ออาหารของครอบครัว</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Sarabun', 'Prompt', sans-serif;
            background: linear-gradient(135deg, #FFE5F1 0%, #FFF0F5 50%, #E6E6FA 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.98);
            border-radius: 25px;
            padding: 40px;
            box-shadow: 0 15px 35px rgba(255, 182, 193, 0.2);
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            padding-bottom: 30px;
            border-bottom: 3px solid #FFE0EC;
        }

        .header h1 {
            color: #D8627D;
            font-size: 2.8em;
            margin-bottom: 15px;
            font-weight: bold;
            text-shadow: 2px 2px 4px rgba(255, 182, 193, 0.3);
        }
        
        .header .subtitle {
            color: #F9A8D4;
            font-size: 1.4em;
            margin-bottom: 10px;
            font-weight: 600;
        }

        .header .tagline {
            color: #A78BFA;
            font-size: 1.1em;
            line-height: 1.6;
            max-width: 700px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .input-section {
            background: linear-gradient(135deg, #FFEDF0, #F0F4FD);
            padding: 35px;
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 8px 20px rgba(255, 182, 193, 0.15);
        }

        .input-section h2 {
            color: #D8627D;
            margin-bottom: 25px;
            font-size: 1.6em;
            text-align: center;
        }

        .ingredients-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 25px;
        }

        .ingredient-input {
            position: relative;
        }

        .ingredient-input input {
            width: 100%;
            padding: 14px 15px 14px 45px;
            border: 2px solid #FFD4E5;
            border-radius: 15px;
            font-size: 1.1em;
            transition: all 0.3s;
            background: linear-gradient(to right, #FFFBFC, #FFF9FC);
        }

        .ingredient-input input:focus {
            outline: none;
            border-color: #F9A8D4;
            box-shadow: 0 0 15px rgba(249, 168, 212, 0.2);
            background: white;
        }

        .ingredient-number {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            width: 24px;
            height: 24px;
            background: linear-gradient(135deg, #FEC8D8, #FFDFD8);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: #D8627D;
            font-size: 0.9em;
        }

        .btn-generate {
            background: linear-gradient(135deg, #F9A8D4, #C084FC);
            color: white;
            border: none;
            padding: 18px 50px;
            font-size: 1.3em;
            border-radius: 35px;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 8px 20px rgba(249, 168, 212, 0.3);
            display: block;
            margin: 35px auto;
            font-weight: bold;
            letter-spacing: 0.5px;
        }

        .btn-generate:hover {
            transform: translateY(-3px);
            box-shadow: 0 12px 25px rgba(249, 168, 212, 0.4);
            background: linear-gradient(135deg, #FBB6CE, #DDA5FF);
        }

        .btn-generate:active {
            transform: translateY(-1px);
        }

        .menu-results {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .menu-card {
            background: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(255, 182, 193, 0.15);
            transition: transform 0.3s;
            border: 2px solid #FFE8F1;
        }

        .menu-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(255, 182, 193, 0.25);
        }

        .menu-card-header {
            padding: 20px;
            color: white;
            font-weight: bold;
            font-size: 1.3em;
            text-align: center;
        }

        .menu-card.soup .menu-card-header {
            background: linear-gradient(135deg, #B4E7F8, #A8DADC);
        }

        .menu-card.dry .menu-card-header {
            background: linear-gradient(135deg, #FFD4BA, #FFDAB9);
        }

        .menu-card-body {
            padding: 25px;
        }

        .menu-name {
            font-size: 1.6em;
            color: #D8627D;
            margin-bottom: 12px;
            font-weight: bold;
        }

        .price-estimate {
            display: inline-block;
            background: linear-gradient(135deg, #FFE5F1, #FCE4EC);
            padding: 8px 16px;
            border-radius: 20px;
            color: #C2185B;
            font-weight: bold;
            margin-bottom: 15px;
            font-size: 1.1em;
        }

        .menu-description {
            color: #666;
            line-height: 1.6;
            margin-bottom: 20px;
            font-size: 1.05em;
        }

        .menu-ingredients {
            background: linear-gradient(135deg, #FFF9FC, #FFF5F9);
            padding: 18px;
            border-radius: 15px;
            margin-bottom: 20px;
            border: 1px solid #FFE8F1;
        }

        .menu-ingredients h4 {
            color: #D8627D;
            margin-bottom: 12px;
            font-size: 1.1em;
        }

        .menu-ingredients ul {
            list-style: none;
            padding-left: 0;
        }

        .menu-ingredients li {
            padding: 6px 0;
            color: #666;
            display: flex;
            align-items: center;
        }

        .menu-ingredients li::before {
            content: '✨';
            margin-right: 10px;
        }

        .cooking-method {
            background: linear-gradient(135deg, #F0F9FF, #F8F0FF);
            padding: 18px;
            border-radius: 15px;
            margin-bottom: 20px;
            border: 1px solid #E8D6FF;
        }

        .cooking-method h4 {
            color: #9F7AEA;
            margin-bottom: 12px;
            font-size: 1.1em;
        }

        .cooking-method ol {
            padding-left: 20px;
            color: #666;
            line-height: 1.8;
        }

        .cooking-method li {
            margin-bottom: 8px;
        }

        .nutrition-info {
            display: flex;
            justify-content: space-around;
            padding: 15px;
            background: linear-gradient(135deg, #FFF0F5, #F5F0FF);
            border-radius: 15px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .nutrition-item {
            text-align: center;
            flex: 1;
            min-width: 80px;
        }

        .nutrition-item .label {
            color: #A78BFA;
            font-size: 0.9em;
            margin-bottom: 5px;
        }

        .nutrition-item .value {
            color: #7C3AED;
            font-weight: bold;
            font-size: 1.1em;
        }

        .taste-indicator {
            display: inline-block;
            padding: 6px 18px;
            border-radius: 25px;
            color: white;
            font-weight: bold;
            margin: 10px 5px;
            font-size: 0.95em;
        }

        .taste-mild {
            background: linear-gradient(135deg, #C7F2E3, #B2E1D4);
            color: #059669;
        }

        .taste-strong {
            background: linear-gradient(135deg, #FECACA, #FCA5A5);
            color: #DC2626;
        }

        .loading {
            display: none;
            text-align: center;
            padding: 50px;
        }

        .loading.active {
            display: block;
        }

        .spinner {
            border: 4px solid #FFE8F1;
            border-top: 4px solid #F9A8D4;
            border-radius: 50%;
            width: 60px;
            height: 60px;
            animation: spin 1s linear infinite;
            margin: 0 auto 25px;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .tips-section {
            background: linear-gradient(135deg, #FFEDF0, #F0F4FD);
            padding: 30px;
            border-radius: 20px;
            margin-top: 35px;
            border: 2px solid #FFE0EC;
        }

        .tips-section h3 {
            color: #D8627D;
            margin-bottom: 18px;
            font-size: 1.4em;
        }

        .tips-section ul {
            list-style: none;
            padding: 0;
        }

        .tips-section li {
            padding: 10px 0;
            color: #666;
            line-height: 1.6;
        }

        .tips-section li::before {
            content: '🌸 ';
            margin-right: 10px;
        }

        .footer {
            text-align: center;
            margin-top: 40px;
            padding-top: 30px;
            border-top: 2px solid #FFE0EC;
            color: #A78BFA;
            font-size: 0.95em;
        }

        @media (max-width: 768px) {
            .container {
                padding: 20px;
            }

            .header h1 {
                font-size: 2em;
            }

            .header .subtitle {
                font-size: 1.2em;
            }

            .header .tagline {
                font-size: 1em;
            }

            .menu-results {
                grid-template-columns: 1fr;
            }

            .ingredients-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🏡 Happy Home Recipes</h1>
            <div class="subtitle">สร้างความสุขในทุกมื้ออาหารของครอบครัว</div>
            <p class="tagline">เพียงแค่บอก 'วัตถุดิบที่คุณมี' เราพร้อมออกแบบสูตรอาหารโฮมเมดง่าย ๆ<br>ที่เติมเต็มความอบอุ่น และกลายเป็นจานโปรดที่เหมาะสมกับทุกวัยในครอบครัว</p>
        </div>

        <div class="input-section">
            <h2>🛒 วัตถุดิบที่คุณมีในครัว (กรอก 5 รายการ)</h2>
            <div class="ingredients-grid">
                <div class="ingredient-input">
                    <span class="ingredient-number">1</span>
                    <input type="text" id="ingredient1" placeholder="เช่น ไก่, หมู, ปลา" />
                </div>
                <div class="ingredient-input">
                    <span class="ingredient-number">2</span>
                    <input type="text" id="ingredient2" placeholder="เช่น ผักบุ้ง, คะน้า" />
                </div>
                <div class="ingredient-input">
                    <span class="ingredient-number">3</span>
                    <input type="text" id="ingredient3" placeholder="เช่น มะเขือเทศ, หอม" />
                </div>
                <div class="ingredient-input">
                    <span class="ingredient-number">4</span>
                    <input type="text" id="ingredient4" placeholder="เช่น ไข่, เต้าหู้" />
                </div>
                <div class="ingredient-input">
                    <span class="ingredient-number">5</span>
                    <input type="text" id="ingredient5" placeholder="เช่น เห็ด, ถั่วฝักยาว" />
                </div>
            </div>
            <button class="btn-generate" onclick="generateMenu()">✨ สร้างเมนูอาหาร</button>
        </div>

        <div class="loading" id="loading">
            <div class="spinner"></div>
            <p style="color: #F9A8D4; font-size: 1.2em; font-weight: bold;">กำลังสร้างสรรค์เมนูอาหารแสนอร่อย...</p>
        </div>

        <div class="menu-results" id="menuResults"></div>

        <div class="tips-section">
            <h3>💝 เคล็ดลับการทำอาหารให้ครอบครัว</h3>
            <ul>
                <li>เลือกวัตถุดิบสดใหม่ เพื่อคุณค่าทางโภชนาการที่ดีที่สุด</li>
                <li>ปรุงรสพอดี ไม่เค็มหรือหวานจัด เพื่อสุขภาพที่ดีของทุกคน</li>
                <li>ใส่ผักหลากสีในทุกมื้อ เพื่อวิตามินและแร่ธาตุที่หลากหลาย</li>
                <li>ทำอาหารด้วยความรัก อาหารจะอร่อยและอบอุ่นยิ่งขึ้น</li>
                <li>ชวนทุกคนมาช่วยทำอาหาร สร้างความสุขและความผูกพันในครอบครัว</li>
            </ul>
        </div>

        <div class="footer">
            <p>Made with 💕 for Happy Families | อาหารดี ชีวิตดี ครอบครัวมีความสุข</p>
        </div>
    </div>

    <script>
        function generateMenu() {
            // เก็บค่าวัตถุดิบ
            const ingredients = [];
            for (let i = 1; i <= 5; i++) {
                const ingredient = document.getElementById(`ingredient${i}`).value.trim();
                if (ingredient) {
                    ingredients.push(ingredient);
                }
            }

            if (ingredients.length < 3) {
                alert('กรุณากรอกวัตถุดิบอย่างน้อย 3 รายการค่ะ 😊');
                return;
            }

            // แสดง loading
            document.getElementById('loading').classList.add('active');
            document.getElementById('menuResults').innerHTML = '';

            // จำลองการประมวลผล
            setTimeout(() => {
                // สร้างเมนูตามวัตถุดิบที่กรอก
                const menus = createMenusFromIngredients(ingredients);
                
                // แสดงผล
                document.getElementById('loading').classList.remove('active');
                document.getElementById('menuResults').innerHTML = menus.join('');
            }, 2000);
        }

        function createMenusFromIngredients(ingredients) {
            // ฐานข้อมูลเมนูตัวอย่างที่จะปรับตามวัตถุดิบ
            const menuTemplates = {
                soup: {
                    mild: [
                        {
                            name: "ต้มจืด{ingredient1}ใส่{ingredient2}",
                            base: "ต้มจืด",
                            cookingSteps: [
                                "ต้มน้ำให้เดือด ใส่กระดูกหมูหรือไก่ (ถ้ามี) เคี่ยว 15 นาที",
                                "ใส่{ingredient1} ที่หั่นเป็นชิ้นพอคำ ต้มประมาณ 5-7 นาที",
                                "ใส่{ingredient2} ต้มต่ออีก 3-5 นาที",
                                "ปรุงรสด้วยซีอิ๊วขาว เกลือเล็กน้อย",
                                "โรยต้นหอม ผักชีซอย เสิร์ฟร้อนๆ"
                            ],
                            portions: "สำหรับ 3-4 ที่",
                            estimatePrice: "40-50"
                        },
                        {
                            name: "แกงจืด{ingredient1}{ingredient3}",
                            base: "แกงจืด",
                            cookingSteps: [
                                "ต้มน้ำซุปกระดูกหมู 500 มล. ให้เดือด",
                                "ใส่{ingredient1} ที่เตรียมไว้ รอให้สุก",
                                "เพิ่ม{ingredient3} ต้มต่อ 3-5 นาที",
                                "ปรุงรสอ่อนๆ ด้วยเกลือ ซีอิ๊วขาว",
                                "ตักเสิร์ฟ โรยผักชี พริกไทย"
                            ],
                            portions: "สำหรับ 4 ที่",
                            estimatePrice: "35-45"
                        }
                    ],
                    strong: [
                        {
                            name: "ต้มยำ{ingredient1}น้ำใส",
                            base: "ต้มยำ",
                            cookingSteps: [
                                "ต้มน้ำ 600 มล. ใส่ตะไคร้ทุบ ใบมะกรูด ข่าหั่น",
                                "ใส่{ingredient1} ที่เตรียมไว้ ต้มจนสุก",
                                "ใส่เห็ดฟาง หอมแดง มะเขือเทศ",
                                "ปรุงรสด้วยน้ำมะนาว น้ำปลา น้ำตาลปี๊บ พริกขี้หนูบด",
                                "ชิมรส ปรับตามชอบ โรยผักชี"
                            ],
                            portions: "สำหรับ 3-4 ที่",
                            estimatePrice: "60-70"
                        },
                        {
                            name: "แกงส้ม{ingredient2}ใส่{ingredient1}",
                            base: "แกงส้ม",
                            cookingSteps: [
                                "ละลายน้ำพริกแกงส้ม 2 ช้อนโต๊ะกับน้ำเล็กน้อย",
                                "ต้มน้ำ 500 มล. ใส่น้ำพริกที่ละลายแล้ว",
                                "ใส่{ingredient1} ต้มจนเริ่มสุก",
                                "เพิ่ม{ingredient2} และผักอื่นๆ ตามชอบ",
                                "ปรุงรสด้วยน้ำมะขามเปียก น้ำปลา น้ำตาลปี๊บ"
                            ],
                            portions: "สำหรับ 4 ที่",
                            estimatePrice: "50-60"
                        }
                    ]
                },
                dry: {
                    mild: [
                        {
                            name: "ผัด{ingredient2}ใส่{ingredient1}",
                            base: "ผัดธรรมดา",
                            cookingSteps: [
                                "ตั้งกระทะใส่น้ำมัน 2 ช้อนโต๊ะ",
                                "ใส่กระเทียมสับเจียวให้หอม",
                                "ใส่{ingredient1} ผัดจนสุก",
                                "เพิ่ม{ingredient2} ผัดให้เข้ากัน",
                                "ปรุงรสด้วยซีอิ๊วขาว น้ำตาล เล็กน้อย",
                                "ผัดอีกครั้ง ตักเสิร์ฟร้อนๆ"
                            ],
                            portions: "สำหรับ 2-3 ที่",
                            estimatePrice: "45-55"
                        },
                        {
                            name: "{ingredient1}ย่างสมุนไพร",
                            base: "ย่าง",
                            cookingSteps: [
                                "หมัก{ingredient1}กับกระเทียม พริกไทย รากผักชี",
                                "เติมซีอิ๊วขาว น้ำมันพืช หมักไว้ 30 นาที",
                                "ย่างบนกระทะหรือเตาย่าง ไฟกลาง",
                                "พลิกบ่อยๆ จนสุกทั่วดี",
                                "เสิร์ฟพร้อมน้ำจิ้มแจ่วและผักสด"
                            ],
                            portions: "สำหรับ 3-4 ที่",
                            estimatePrice: "60-80"
                        }
                    ],
                    strong: [
                        {
                            name: "ผัดกะเพรา{ingredient1}",
                            base: "ผัดกะเพรา",
                            cookingSteps: [
                                "โขลกกระเทียม พริกขี้หนู เข้าด้วยกัน",
                                "ตั้งกระทะไฟแรง ใส่น้ำมัน",
                                "ใส่เครื่องที่โขลก เจียวให้หอม",
                                "ใส่{ingredient1} ผัดจนสุก",
                                "ปรุงรสด้วยน้ำปลา ซีอิ๊วดำ น้ำตาล",
                                "ใส่ใบกะเพรา ผัดพอสลด ปิดไฟ"
                            ],
                            portions: "สำหรับ 2 ที่",
                            estimatePrice: "40-50"
                        },
                        {
                            name: "ยำ{ingredient3}ใส่{ingredient1}",
                            base: "ยำ",
                            cookingSteps: [
                                "ลวก{ingredient1}ในน้ำเดือด จนสุก พักให้เย็น",
                                "เตรียม{ingredient3} หั่นเป็นชิ้นบางๆ",
                                "ทำน้ำยำ: โขลกพริก กระเทียม ใส่น้ำปลา น้ำมะนาว น้ำตาลปี๊บ",
                                "คลุกวัตถุดิบทั้งหมดกับน้ำยำ",
                                "ใส่หอมแดง ต้นหอม ผักชีฝรั่ง มะเขือเทศ คลุกเคล้า",
                                "จัดจาน โรยถั่วลิสงคั่ว"
                            ],
                            portions: "สำหรับ 3-4 ที่",
                            estimatePrice: "55-65"
                        }
                    ]
                }
            };

            // สุ่มเลือกเมนูและปรับตามวัตถุดิบ
            const selectedMenus = [];
            
            // สุ่มว่าจะใช้ mild หรือ strong สำหรับแต่ละประเภท
            const soupType = Math.random() > 0.5 ? 'mild' : 'strong';
            const dryType = soupType === 'mild' ? 'strong' : 'mild';
            
            // เลือกเมนูน้ำ
            const soupMenus = menuTemplates.soup[soupType];
            const selectedSoup = soupMenus[Math.floor(Math.random() * soupMenus.length)];
            
            // เลือกเมนูแห้ง
            const dryMenus = menuTemplates.dry[dryType];
            const selectedDry = dryMenus[Math.floor(Math.random() * dryMenus.length)];

            // สร้างการ์ดเมนู
            selectedMenus.push(createDetailedMenuCard(selectedSoup, 'soup', soupType, ingredients));
            selectedMenus.push(createDetailedMenuCard(selectedDry, 'dry', dryType, ingredients));

            return selectedMenus;
        }

        function createDetailedMenuCard(template, type, taste, ingredients) {
            // แทนที่ placeholder ด้วยวัตถุดิบจริง
            let menuName = template.name;
            let cookingSteps = [...template.cookingSteps];
            
            // แทนที่วัตถุดิบในชื่อและขั้นตอน
            for (let i = 0; i < ingredients.length && i < 5; i++) {
                const placeholder = `{ingredient${i + 1}}`;
                menuName = menuName.replace(placeholder, ingredients[i]);
                cookingSteps = cookingSteps.map(step => 
                    step.replace(new RegExp(placeholder, 'g'), ingredients[i])
                );
            }

            // กำหนดข้อมูลเพิ่มเติม
            const typeText = type === 'soup' ? '🍲 อาหารประเภทน้ำ' : '🍳 อาหารประเภทแห้ง';
            const tasteClass = taste === 'mild' ? 'taste-mild' : 'taste-strong';
            const tasteText = taste === 'mild' ? '😊 รสอ่อน เหมาะกับทุกวัย' : '🌶️ รสจัด กลมกล่อม';

            // สร้างรายการวัตถุดิบที่ใช้
            const usedIngredients = ingredients.slice(0, Math.min(4, ingredients.length));

            return `
                <div class="menu-card ${type}">
                    <div class="menu-card-header">
                        ${typeText}
                    </div>
                    <div class="menu-card-body">
                        <div class="menu-name">${menuName}</div>
                        <span class="taste-indicator ${tasteClass}">${tasteText}</span>
                        <div class="price-estimate">💰 ประมาณ ${template.estimatePrice} บาท</div>
                        
                        <div class="menu-ingredients">
                            <h4>📝 วัตถุดิบที่ใช้ (${template.portions})</h4>
                            <ul>
                                ${usedIngredients.map((ing, index) => {
                                    const amounts = ['200 กรัม', '150 กรัม', '100 กรัม', '50 กรัม'];
                                    return `<li>${ing} - ${amounts[index]}</li>`;
                                }).join('')}
                                <li>เครื่องปรุงพื้นฐาน (กระเทียม, น้ำปลา, น้ำมัน)</li>
                            </ul>
                        </div>

                        <div class="cooking-method">
                            <h4>👩‍🍳 วิธีทำ</h4>
                            <ol>
                                ${cookingSteps.map(step => `<li>${step}</li>`).join('')}
                            </ol>
                        </div>

                        <div class="nutrition-info">
                            <div class="nutrition-item">
                                <div class="label">⏰ เวลา</div>
                                <div class="value">15-20 นาที</div>
                            </div>
                            <div class="nutrition-item">
                                <div class="label">👥 สำหรับ</div>
                                <div class="value">3-4 คน</div>
                            </div>
                            <div class="nutrition-item">
                                <div class="label">🔥 ระดับ</div>
                                <div class="value">ง่าย</div>
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        // ฟังก์ชันสำหรับ Enter key
        document.addEventListener('DOMContentLoaded', function() {
            const inputs = document.querySelectorAll('.ingredient-input input');
            inputs.forEach(input => {
                input.addEventListener('keypress', function(e) {
                    if (e.key === 'Enter') {
                        generateMenu();
                    }
                });
            });
        });
    </script>
</body>
</html>
