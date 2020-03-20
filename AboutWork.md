# งานที่มีส่วนร่วม
## Opendata Service Platform (Open-D)
- [Open-D](http://opend.openservice.in.th "Open-D")  
- [บทความ Open-D: ข้อมูลเปิดสำหรับชุมชน Application Developers และ Data Scientists](https://www.nectec.or.th/innovation/innovation-software/opendata_2.html "Open-D")  


- ทำในส่วน Visualization ให้กับระบบ
- สร้างแดรชบอร์ด ที่เป็นการรวม Visualize ของชุดข้อมูลต่างๆ ให้ผู้ใช้สร้างเป็นแดรชบอร์ด
- เพิ่มเติมฟังชั่นต่างๆของระบบ และ ดูแลส่วน UI ของหน้าเว็บไซต์
- สร้างเว็บไซต์หรือสื่อข้อมูลในกิจกรรมต่างๆที่เกี่ยวข้อง


### Visualization
สร้าง Visualize หรือกราฟที่สามารถรองรับข้อมูลที่เข้ามาในระบบ และรองรับการใช้เงื่อนไขในการแสดงผลข้อมูลในแต่ละรูปแบบ โดยส่วน Visualize นั้นจะใช้ Library ของ Highchart  โดย ณ ตอนนี้กราฟที่ได้พัฒนา คือ Pie, Bar, Line, Map, Scatter, TreeMap
<div> <img src="https://github.com/angkarn/aboutWork/raw/master/assets/vsl_icon.png" width="500" /></div>

โดยสามารถเข้าถึงได้จาก หน้า [Open-D](https://opend.openservice.in.th/opend "Open-D") เพื่อค้นหาชุดข้อมูลใดๆ และเข้าไปที่ API จากนั้นใส่เงื่อนไขในแบบที่ผู้ใช้ต้องการ เมื่อกดค้นหาจะมี icon ของ Visualize แต่ละแบบที่สามารถเลือกดูได้ปรากฏขึ้นมา
โดยในแต่ละกราฟจะมีการพัฒนาให้สามารถรองรับข้อมูลใดๆ ในฐานข้อมูล และมีวิธีการตรวจสอบข้อมูลที่เข้ามาและการประมวลผลข้อมูลที่แตกต่างกัน

> ทดลองผ่าน iframe สามารถคลิก View full เพื่อดูกราฟจริง หรือคลิกเมนูบนขวาและเลือก View Data ก็จะสามารถดูข้อมูลต้นทางจาก Open-D ได้

#### Bar
เมื่อมีการจัดกลุ่มกราฟ Bar กฌจะสามารถแบ่งกลุ่มให้ผู้ใช้

<iframe src="https://opend.openservice.in.th/opend/Visualization/bar?dsname=vir_11_1519627355&amp;path=vir_11_1519627355&amp;aggf%5b%5d=count&amp;agg_prop%5b%5d=col_2&amp;groupby%5b%5d=col_8&amp;loadAll=1&amp;hideMn=1" style="width: 100%; height: 480px;"></iframe>


#### Map
เช่น หากมีการจัดกลุ่มข้อมูลโดยแบ่งตามจังหวัด ก็จะสามารถใช้ Visualize ที่เป็น Map หรือแผนที่ที่สามารถแสดงความแตกต่างของผลลัพธ์ได้  

และเมื่อข้อมูลนั้นมีถึงระดับอำเภอ หรือแม้แต่ตำบล ก็มีฟังชั่นที่สามารถ Drilldown หรือเป็นการคลิกเลือกที่จังหวัดและสามารถแสดงอำเภอทั้งหมดในจังหวัดนั้น หรือ คลิกที่อำเภอเพื่อแสดงตำบลทั้งหมดในอำเภอพร้อมข้อมูลที่ผู้ใช้ต้องการ

<div> <div class='gif'> <img alt="Map Drilldown" src="https://github.com/angkarn/aboutWork/raw/master/assets/map_drilldown_450.gif" width="480" /></div></div>

<hr/><br/>



<iframe src="https://opend.openservice.in.th/opend/Visualization/map_subdistrict_dd?dsname=vir_6_1519099534&amp;path=vir_6_1519099534&amp;aggf[]=count&amp;agg_prop[]=col_4&amp;groupby[]=col_10&amp;groupby[]=col_9&amp;groupby[]=col_8&amp;province=col_10&amp;district=col_9&amp;subdistrict=col_8&amp;loadAll=1&amp;limit=100&amp;offset=0&amp;hideMn=1" style="width: 100%; height: 480px;"></iframe>
<hr/><br/>

#### Line
เมื่อมีการจัดกลุ่มตามวันที่ไม่ว่าจะเป็น วัน เดือน ปี กราฟเส้น(Line) จะสามารถตรวจสอบรูปแบบของข้อมูลและทำการจัดเรียงข้อมูลออกมาได้ เช่น ปี เดือน หรือแม่แต่รูปแบบวันที่
เช่น 16/10/2561, 16-10-2561, หรือเป็นตัวอักษร 16 ก.ย. 2561 หรือข้อมูลที่ตรวจสอบไม่ได้ในตัวเอง เช่น 9/9/2561 ที่รู้แค่เพียงปีเท่านั้น
ก็จะมีวิธีการตรวจสอบ โดยตรวจสอบจากข้อมูลในชุดเดียวกันว่ามีข้อมูลไหนที่ตรวจสอบรูปแบบได้ทั้งหมด
เช่น เจอข้อมูลอื่นในชุดข้อมูลเดียวกัน คือ 16/4/2561 ก็จะตรวจสอบได้ทันทีว่า ข้อมูลชุดนี้ใช้รูปแบบของวันที่รูปแบบใด
โดยจะตรวจสอบผ่าน javascript โดยมีการใช้ libraries เป็นตัวช่วยอย่าง momentjs

<iframe src="https://opend.openservice.in.th/opend/Visualization/line_date?dsname=vir_56_1520907151&path=vir_56_1520907151&aggf%5b%5d=sum&agg_prop%5b%5d=col_10&groupby%5b%5d=col_2&loadAll=1&hideMn=1" style="width: 100%; height: 480px;"></iframe>
<hr/><br/>
<iframe src="https://opend.openservice.in.th/opend/Visualization/line_date_Mgroup?dsname=vir_56_1520907151&amp;path=vir_56_1520907151&amp;aggf%5b%5d=avg&amp;agg_prop%5b%5d=col_7&amp;orderby=desc&amp;groupby%5b%5d=col_2&amp;groupby%5b%5d=col_3&amp;date=col_2&amp;loadAll=1&amp;3d=0&amp;limit=5000&amp;hideMn=1" style="width: 100%; height: 480px;"></iframe>

#### Scatter
Scatter เป็นกราฟแสดงค่าความแตกต่างโดยใช้แกน X, Y

<iframe src="https://opend.openservice.in.th/opend/Visualization/scatter?dsname=vir_183_1523954300&amp;path=vir_183_1523954300&amp;aggf[]=sum&amp;agg_prop[]=col_8&amp;aggf[]=sum&amp;agg_prop[]=col_20&amp;groupby[]=col_5&amp;loadAll=1&amp;limit=100&amp;offset=0&amp;hideMn=1" style="width: 100%; height: 480px;"></iframe>


#### TreeMap
TreeMap เป็นการแบ่งกลุ่มของข้อมูล ซึ่งได้พัฒนาให้รองรับการจัดกลุ่มได้ทุกระดับ จากตัวอย่างเป็นการจัดกลุ่มที่ลงลึกถึงสามระดับคือ จังหวัด อำเภอ และโรงเรียน ซึ่งสามารถคลิกที่ข้อมูลในแต่ละระดับเพื่อเข้าขึ้นข้อมูลนั้นในระดับย่อยๆได้

<iframe src="https://opend.openservice.in.th/opend/Visualization/treeMap?dsname=vir_183_1523954300&amp;path=vir_183_1523954300&amp;aggf[]=sum&amp;agg_prop[]=col_8&amp;groupby[]=col_5&amp;groupby[]=col_4&amp;groupby[]=col_3&amp;province=col_5&amp;district=col_4&amp;loadAll=1&amp;limit=10000&amp;offset=0&amp;hideMn=1" style="width: 100%; height: 480px;"></iframe>


<hr>

### Dashboard
ความสามารถของ Dashboard คือ การรวม Visualize ต่างๆที่เราได้สร้างออกมา มาจัดรวมอยู่ด้วยกัน และสามารถจัดตำแหน่ง ขนาด รูปแบบต่างๆตามที่ต้องการ และสามารถบันทึกเพื่อแชร์เป็น Public ให้ผู้อื่นเข้ามาดู Dashboard นี้ได้
> จำเป็นต้อง Login และทำการ save Visualize จากหน้า Visualize นั้นๆ เพื่อใช้ใน Dashboard ภายหลัง โดยเข้าไปที่เมนู Dashboard จากหน้า Open-D

##### วิดีโอตัวอย่างการใช้งาน
<video width="100%" height="400" controls>
  <source src="https://github.com/angkarn/aboutWork/raw/master/assets/dashboard.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

้<hr>

### ดูแลและเพิ่มเติมฟังชั่นการใช้งาน
ดูแลและเพิ่มเติมฟังชั่นการใช้งานต่างๆ และการออกแบบ ของระบบ เช่น การจัดการผู้ใช้, ระบบการอัปโหลดและการจัดการชุดข้อมูล,
การตรวจสอบสิทธิ์, UI ของหน้าเว็บไซต์ เป็นต้น

### สร้างสื่อหรือเว็บไซต์ตามกิจกรรมที่เกี่ยวข้อง
- สร้างสื่อเว็บไซต์ให้ข้อมูลด้าน dataset ที่ให้ผู้แข่งขันใช้ในงาน e-Culture Hackathon 2018 > [e-Culture Hackathon 2018](http://www.anurak.in.th/dataset "e-Culture Hackathon 2018")

<br>
<hr>
