# คู่มือหน้าจอ `v_` ของ `mod/newmodule` ฉบับร่าง

Last updated: 2026-07-27

## ขอบเขตเอกสาร

เอกสารนี้สรุปหน้าจอที่ใช้งานจริงของระบบ `v_` ใน `mod/newmodule` เพื่อใช้เป็นคู่มืออ้างอิงสำหรับผู้ใช้และผู้ดูแลระบบ

ครอบคลุม:
- หน้าจอหลักที่เปิดใช้งานจริง
- ปุ่ม, ลิงก์, ฟอร์ม, และ flow การใช้งาน
- ตารางฐานข้อมูลที่เกี่ยวข้องกับแต่ละหน้าจอ
- หน้าจอรายละเอียดของนักศึกษา
- หน้าจอจัดการ curriculum / course / student / research / soft skills / NTS / report

ไม่เน้น:
- ไฟล์ backup หรือ dated copy เช่น `*250923.php`, `*260224.php`, `*260526*.php`, `*bk*.php`
- helper/API ที่ไม่ใช่หน้าจอหลัก ยกเว้นกรณีที่เกี่ยวกับปุ่มบนหน้าโดยตรง

## วิธีใช้เอกสารนี้

สำหรับแต่ละหน้าจอ จะมี 5 ส่วน:
- จุดประสงค์
- ปุ่ม/ตัวควบคุม
- ขั้นตอนการใช้งาน
- ตารางที่เกี่ยวข้อง
- หมายเหตุสำคัญ

---

## ภาพรวมหน้าจอหลัก

| ID | หน้าจอ | ไฟล์ | ประเภท | ผู้ใช้หลัก | หน้าที่หลัก |
|---|---|---|---|---|---|
| S01 | หน้าแรก | `v_index.php` | Dashboard | Admin / Staff | เลือก curriculum และดู summary |
| S02 | จัดการหลักสูตร | `v_curriculum_management.php` | Hub | Admin / Staff | รวมทางลัดไปยังงานจัดการหลักสูตร |
| S03 | จัดการรายวิชาในหลักสูตร | `v_manage_cur_course.php` | Edit | Admin / Staff | เพิ่ม/ลบรายวิชาและ lock curriculum |
| S04 | จัดการนักศึกษาในหลักสูตร | `v_manage_cur_student.php` | Edit | Admin / Staff | เลือกนักศึกษาเข้าหลักสูตร |
| S05 | จัดการข้อมูลนักศึกษาและการลงทะเบียน | `v_manage_cur_student_detail.php` | Edit | Admin / Staff | แก้ข้อมูลนักศึกษาและดู registration |
| S06 | SoftSkills dashboard | `v_softskills.php` | Dashboard | Admin / Staff | สรุป Soft Skills / English / Spider chart |
| S07 | จัดการ Soft Skills & English Scores | `v_manage_softskills.php` | Edit | Admin / Staff | บันทึกคะแนน Soft Skills และ English |
| S08 | Non-Technical Skills dashboard | `v_nts.php` | Dashboard | Admin / Staff | สรุป NTS ของนักศึกษา |
| S09 | ดูข้อมูล NTS ของนักศึกษา | `v_view_student_nts.php` | Detail | Admin / Staff | ดูรายละเอียด NTS รายคน |
| S10 | Research dashboard | `v_research.php` | Dashboard | Admin / Staff | ติดตามงาน research / task |
| S11 | ดูข้อมูล Task และ Alert ของนักศึกษา | `v_view_student_research.php` | Detail | Admin / Staff | ดู task และแจ้งเตือนรายคน |
| S12 | สร้างรายงาน | `v_view_report.php` | Report | Admin / Staff | ค้นหา/กรอง/ส่งออก CSV |
| S13 | ดูข้อมูลการลงทะเบียนนักศึกษา | `v_view_student_courses.php` | Detail | Admin / Staff | ดูทะเบียนเรียนรายคน |
| S14 | ดูรายละเอียดคะแนน Knowledge | `v_view_student_knowledge.php` | Detail | Admin / Staff | ดูคะแนน Knowledge และ CE |

---

## S01: `v_index.php`

### จุดประสงค์
- เป็นหน้าเริ่มต้นของระบบ
- เลือกหลักสูตรผ่าน dropdown
- แสดง dashboard คะแนน Mile Point ของหลักสูตรที่เลือก
- เป็นจุดกระโดดไปหน้าจัดการหลักสูตร, student, research, softskills, nts และ summary อื่น ๆ

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| Curriculum dropdown | เลือก `setid` เพื่อเปลี่ยนบริบทของหลักสูตร |
| ลิงก์ใน dashboard | เปิดหน้าสรุปหรือรายละเอียดตามหัวข้อ เช่น Knowledge / Research / SoftSkills / NTS |
| ลิงก์จัดการนักศึกษา | ไป `v_manage_cur_student.php` |
| ลิงก์จัดการข้อมูลลงทะเบียน | ไป `v_sync_data_management.php` |
| ลิงก์จัดการโครงสร้างหลักสูตร | ไป `v_manage_cur_course.php` |

### ขั้นตอนการใช้งาน
1. เปิดหน้า `v_index.php`
2. เลือกหลักสูตรจาก dropdown
3. ตรวจดู dashboard คะแนนรวมของหลักสูตร
4. คลิกหัวข้อย่อยเพื่อเข้าไปดู detail ของแต่ละด้าน
5. ถ้าต้องจัดการหลักสูตร ให้ใช้ลิงก์ทางลัดด้านบน

### ตารางที่เกี่ยวข้อง
- อ่าน `mdl_a_curset`
- อ่าน `mdl_user_student`
- อ่าน `mdl_milepoint_view`
- อ่าน view ที่แตกจาก `sql/create_milepoint_views.sql`

### หมายเหตุสำคัญ
- หน้า นี้ถูกป้องกันด้วยสิทธิ์ admin ในโค้ดปัจจุบัน
- ถ้าไม่ใช่ admin จะถูก redirect ออก
- หน้านี้เป็นจุดสำคัญของ flow ทั้งระบบ ดังนั้น manual ควรใส่ภาพหน้าจอหน้าแรกไว้เป็นหน้าเปิดเล่ม

---

## S02: `v_curriculum_management.php`

### จุดประสงค์
- เป็นหน้ารวมงานจัดการ curriculum
- แสดง summary ของนักศึกษาในหลักสูตร
- มีทางลัดไปงานจัดการ student, sync, และ course

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| `จัดการนักศึกษาในหลักสูตร` | เปิด `v_manage_cur_student.php` |
| `จัดการข้อมูลลงทะเบียน` | เปิด `v_sync_data_management.php` |
| `จัดการโครงสร้างหลักสูตร` | เปิด `v_manage_cur_course.php` |
| ลิงก์รหัสนักศึกษาในตาราง | เปิด `v_view_student_courses.php` |
| ไอคอนแก้ไข | เปิด `v_manage_cur_student_detail.php` |

### ขั้นตอนการใช้งาน
1. เข้า `v_curriculum_management.php`
2. เลือก curriculum ที่ต้องการ
3. ตรวจดูข้อมูลสรุปใน dashboard
4. ใช้ทางลัดเพื่อไปยังหน้าจัดการที่ต้องการ
5. คลิกรหัสนักศึกษาเพื่อดูรายละเอียดลงทะเบียนรายคน

### ตารางที่เกี่ยวข้อง
- อ่าน `mdl_a_curset`
- อ่าน `mdl_user_student`
- อ่าน `mdl_milepoint_view`

### หมายเหตุสำคัญ
- หน้านี้เป็น hub ที่เหมาะสำหรับใส่ใน manual เป็น “จุดศูนย์กลาง”
- ถ้าคนอ่านใหม่ ให้เริ่มจากหน้านี้จะเข้าใจ flow ทั้งระบบเร็วที่สุด

---

## S03: `v_manage_cur_course.php`

### จุดประสงค์
- จัดการรายวิชาที่อยู่ในโครงสร้างหลักสูตร
- เปิด/ปิด lock ของหลักสูตร
- บันทึกรายวิชาที่ควรอยู่ใน curriculum

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| `ปลดล็อคหลักสูตร` / `ล็อคหลักสูตร` | เปลี่ยนสถานะ lock ของ curriculum |
| Checkbox ของรายวิชา | เลือกหรือยกเลิกรายวิชาในหลักสูตร |
| `บันทึกโครงสร้างหลักสูตร` | บันทึกการเปลี่ยนแปลงรายวิชา |
| Breadcrumb กลับหน้าเดิม | ย้อนกลับไป `v_curriculum_management.php` หรือ `v_index.php` |

### ขั้นตอนการใช้งาน
1. เปิดหน้าจัดการรายวิชา
2. ตรวจดูว่าหลักสูตรถูก lock อยู่หรือไม่
3. ถ้ายังเปิดอยู่ ให้ติ๊กเลือกวิชาที่ต้องการ
4. กดบันทึก
5. ถ้าต้องการปิดการแก้ไข ให้กด lock หลักสูตร

### ตารางที่เกี่ยวข้อง
- อ่าน `mdl_a_curset`
- อ่าน `mdl_course_ep`
- อ่าน `mdl_cur_course`

### หมายเหตุสำคัญ
- ถ้าหลักสูตรถูก lock ปุ่มบางส่วนจะซ่อนหรือ disabled
- คู่มือควรอธิบายให้ชัดว่า lock มีผลกับการแก้ไขต่อจากหน้านี้

---

## S04: `v_manage_cur_student.php`

### จุดประสงค์
- เลือกนักศึกษาที่อยู่ในหลักสูตร
- แสดงรายชื่อนักศึกษาแบบเลือกได้
- บันทึกการเปลี่ยนแปลง membership ของ curriculum

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| Checkbox รายชื่อนักศึกษา | เลือกนักศึกษาที่จะอยู่ในหลักสูตร |
| `บันทึกการเปลี่ยนแปลง` | บันทึกการเลือกนักศึกษา |
| ลิงก์รหัสนักศึกษา | เปิด `v_manage_cur_student_detail.php` |

### ขั้นตอนการใช้งาน
1. เปิดหน้าจัดการนักศึกษาในหลักสูตร
2. ตรวจดูรายชื่อนักศึกษาที่มีสถานะ current / available / other
3. ติ๊ก checkbox เฉพาะคนที่ต้องการ
4. กดบันทึกการเปลี่ยนแปลง
5. ถ้าต้องการแก้ข้อมูลรายคน ให้กดรหัสนักศึกษาเพื่อไปหน้ารายละเอียด

### ตารางที่เกี่ยวข้อง
- อ่านและอัปเดต `mdl_user_student`

### หมายเหตุสำคัญ
- หน้านี้เป็นจุดที่ใช้ยืนยันว่าใครอยู่ใน curriculum
- คู่มือควรอธิบายสถานะ `current`, `available`, `other` ให้ผู้ใช้เข้าใจว่าแต่ละสีหมายถึงอะไร

---

## S05: `v_manage_cur_student_detail.php`

### จุดประสงค์
- แก้ไขข้อมูลนักศึกษา
- ดูสรุปการลงทะเบียนของนักศึกษาคนนั้น

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| `studyplan` dropdown | เลือกแผนการเรียน |
| `advisor` textbox | กรอกชื่ออาจารย์ที่ปรึกษา |
| `cohort` number input | ระบุรุ่นของนักศึกษา |
| `บันทึกข้อมูลนักศึกษา` | บันทึกข้อมูลที่แก้ไข |

### ขั้นตอนการใช้งาน
1. เปิดหน้ารายละเอียดจากรายชื่อนักศึกษา
2. ตรวจข้อมูลปัจจุบันของนักศึกษา
3. แก้ `studyplan`, `advisor`, และ `cohort` ตามต้องการ
4. กดบันทึกข้อมูลนักศึกษา
5. เลื่อนดูสรุปการลงทะเบียนด้านล่างเพื่อยืนยันข้อมูลประกอบ

### ตารางที่เกี่ยวข้อง
- อ่าน/เขียน `mdl_user_student`
- อ่าน `mdl_student_registered_course`
- อ่าน `mdl_student_registration_term`
- อ่าน `mdl_course_ep`

### หมายเหตุสำคัญ
- ส่วนสรุปการลงทะเบียนด้านล่างเป็น read-only
- หากข้อมูลส่วนนี้ไม่ขึ้น ควรตรวจ `setid` และ `sid` ก่อน

---

## S06: `v_softskills.php`

### จุดประสงค์
- แสดง dashboard คะแนน Soft Skills และ English ที่รวมอยู่ใน Mile Point
- แสดง spider chart สำหรับภาพรวมของนักศึกษาในหลักสูตร
- เป็นทางเข้าหน้าแก้ไข SoftSkills ของแต่ละคน

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| Curriculum dropdown | เลือกหลักสูตร |
| `จัดการ EnglihSkills` | เปิดหน้าจัดการ English/Soft Skills |
| ลิงก์รหัสนักศึกษา | เปิด `v_manage_softskills.php` ของคนนั้น |

### ขั้นตอนการใช้งาน
1. เปิดหน้า softskills dashboard
2. เลือก curriculum
3. ตรวจดูคะแนนรวมและกราฟ
4. คลิกนักศึกษาที่ต้องการเพื่อไปหน้าจัดการรายคน

### ตารางที่เกี่ยวข้อง
- อ่าน `mdl_user_student`
- อ่าน `mdl_student_softskill_result`
- อ่าน `mdl_student_english_test_result`
- อ่าน `mdl_student_english_test_score_details`
- อ่าน `mdl_english_test_criteria`
- อ่าน `mdl_milepoint_view`

### หมายเหตุสำคัญ
- หน้านี้ควรอธิบายแนวคิด “Softskills + English = ส่วนหนึ่งของ Mile Point”
- หน้าใช้ทั้ง read-only dashboard และ link ไปหน้าจัดการ

---

## S07: `v_manage_softskills.php`

### จุดประสงค์
- บันทึกผล Soft Skills ของนักศึกษา
- บันทึกผล English test / score details
- เป็นหน้าจัดการข้อมูลจริง ไม่ใช่แค่แสดงผล

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| Search input | ค้นหานักศึกษา |
| `ค้นหา` | เริ่มค้นหา |
| `ล้าง` | เคลียร์เงื่อนไขค้นหา |
| Checkbox ของ soft skill | เลือกสกิลที่ผ่าน |
| `บันทึก Soft Skills` | บันทึกผล soft skill |
| `บันทึก English Scores` | บันทึกคะแนน English |

### ขั้นตอนการใช้งาน
1. เลือกหรือค้นหานักศึกษา
2. ตรวจข้อมูลเดิมที่ระบบโหลดมาให้
3. ติ๊ก soft skill ที่ผ่าน
4. กรอกหรือปรับ English score ตามฟอร์ม
5. กดบันทึก Soft Skills หรือบันทึก English Scores ตามส่วนที่แก้

### ตารางที่เกี่ยวข้อง
- อ่าน/เขียน `mdl_student_softskill_result`
- อ่าน/เขียน `mdl_student_english_test_result`
- อ่าน/เขียน `mdl_student_english_test_score_details`
- อ่าน `mdl_english_test_criteria`

### หมายเหตุสำคัญ
- หน้านี้ควรระวังเรื่อง validation ของคะแนนและวันที่
- ถ้าจะใส่คู่มือจริง ควรมีภาพตัวอย่างสองส่วน: Soft Skills และ English Scores

---

## S08: `v_nts.php`

### จุดประสงค์
- แสดงภาพรวมคะแนน Non-Technical Skills ของนักศึกษาในหลักสูตร
- ค้นหานักศึกษาตามรหัสหรือชื่อ
- เปิด detail ของนักศึกษารายคน

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| Search input | ค้นหานักศึกษา |
| `ค้นหา` | โหลด summary ใหม่ |
| `ล้าง` | เคลียร์คำค้น |
| ลิงก์รหัสนักศึกษาในตาราง | เปิด `v_view_student_nts.php` |

### ขั้นตอนการใช้งาน
1. เข้า dashboard NTS
2. เลือก curriculum
3. พิมพ์คำค้นหาถ้าต้องการกรอง
4. กดค้นหาหรือกด Enter
5. คลิกนักศึกษาที่สนใจเพื่อดู detail

### ตารางที่เกี่ยวข้อง
- อ่าน `mdl_user_student`
- อ่าน `mdl_nts_scores`
- อ่าน `mdl_student_registered_course`
- อ่าน `mdl_student_registration_term`
- อ่าน `mdl_course_ep`

### หมายเหตุสำคัญ
- ตารางสรุปนี้มักโหลดผ่าน JavaScript / API
- คู่มือควรบอกให้ชัดว่าผู้ใช้ต้องเลือก curriculum ก่อนจึงจะเห็นผลลัพธ์ที่ถูกต้อง

---

## S09: `v_view_student_nts.php`

### จุดประสงค์
- แสดง NTS รายคนแบบละเอียด
- แสดงทั้งภาพรวม, รายวิชา, และกิจกรรม Research Progress Meeting
- เปิดทางไปแก้ไขคะแนน NTS

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| `แก้ไข/บันทึกคะแนน NTS` | เปิด `v_edit_student_nts.php` |
| Breadcrumb back | กลับหน้ารวม NTS |

### ขั้นตอนการใช้งาน
1. เปิดจาก dashboard NTS ของนักศึกษารายคน
2. ตรวจข้อมูลโปรไฟล์นักศึกษา
3. ตรวจ summary คะแนนและตารางรายละเอียด
4. ถ้าต้องแก้ไข ให้กดปุ่ม edit

### ตารางที่เกี่ยวข้อง
- อ่าน `mdl_user_student`
- อ่าน `mdl_nts_scores`
- อ่าน `mdl_student_registered_course`
- อ่าน `mdl_student_registration_term`
- อ่าน `mdl_course_ep`
- อ่าน `mdl_nts_research_progress`

### หมายเหตุสำคัญ
- หน้านี้เป็น read-heavy page
- คู่มือควรเน้นวิธีอ่านค่า “ผ่าน/ไม่ผ่าน” และการตีความเปอร์เซ็นต์

---

## S10: `v_research.php`

### จุดประสงค์
- แสดง dashboard ติดตาม research / task ของนักศึกษา
- เปิดทางไปจัดการรายการประเมินและดูรายละเอียดนักศึกษา

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| `จัดการรายการประเมิน Research` | เปิด `v_list_tasks_research.php` |
| ลิงก์รหัสนักศึกษา | เปิด `v_view_student_research.php` |
| ปุ่ม `จัดการ` | เปิด `v_manage_student_research.php` |

### ขั้นตอนการใช้งาน
1. เปิดหน้า research dashboard
2. เลือก curriculum
3. ตรวจสรุปความคืบหน้าของนักศึกษา
4. เปิดรายละเอียดรายคนหรือไปหน้าจัดการรายการประเมิน

### ตารางที่เกี่ยวข้อง
- อ่าน `mdl_user_student`
- อ่าน `mdl_student_tasks`
- อ่าน `mdl_a_tasks`
- อ่าน summary view ที่เกี่ยวข้องกับ research / milepoint

### หมายเหตุสำคัญ
- หน้านี้ควรสื่อให้ชัดว่าเป็น “ติดตามงาน” ไม่ใช่แค่ list task เฉย ๆ

---

## S11: `v_view_student_research.php`

### จุดประสงค์
- แสดง task และ alert ของนักศึกษาแบบรายคน
- ใช้ดูว่ามีงานอะไร ค้างอะไร และแจ้งเตือนเมื่อไร

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| `Dashboard` | กลับหน้ารวม research |
| Breadcrumb | กลับหน้า parent ได้รวดเร็ว |

### ขั้นตอนการใช้งาน
1. เปิดจาก research dashboard
2. ดูข้อมูลโปรไฟล์นักศึกษา
3. ตรวจตาราง task และ alert
4. ถ้าต้องกลับภาพรวม ให้กด Dashboard

### ตารางที่เกี่ยวข้อง
- อ่าน `mdl_student_tasks`
- อ่าน `mdl_a_tasks`
- อ่าน `mdl_user_student`

### หมายเหตุสำคัญ
- เป็นหน้า detail แบบ read-only
- เหมาะสำหรับใช้แนบภาพตัวอย่างในคู่มือเพราะตารางมีคอลัมน์เยอะ

---

## S12: `v_view_report.php`

### จุดประสงค์
- สร้างรายงานแบบกรองเงื่อนไข
- แสดงข้อมูล student summary พร้อม Knowledge / Research / Soft skills / NTS
- ส่งออก CSV เพื่อใช้ภายนอกระบบ

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| Filter ปี | กรองรายงานตามปี |
| Filter สถานะนักศึกษา | กรองตามสถานะ |
| Filter ปีที่เริ่มเรียน | กรองตาม cohort ปีเริ่ม |
| Filter แผนการเรียน | กรองตาม `ก` / `ข` |
| `ค้นหา` | รัน filter |
| `รีเซ็ต` | ล้าง filter ทั้งหมด |
| `Export Data as Excel (CSV)` | ดาวน์โหลดรายงานเป็น CSV |

### ขั้นตอนการใช้งาน
1. เข้าเมนูรายงาน
2. เลือกเงื่อนไขที่ต้องการ
3. กดค้นหา
4. ตรวจผลลัพธ์ในตาราง
5. ถ้าต้องเอาไปใช้ภายนอก ให้กด export CSV

### ตารางที่เกี่ยวข้อง
- อ่าน `mdl_user_student`
- อ่าน summary views จาก `mdl_milepoint_view`

### หมายเหตุสำคัญ
- หน้านี้เหมาะสำหรับอธิบายเรื่อง filter ก่อน เพราะเป็นหน้าที่มีผลต่อข้อมูลที่ผู้ใช้เห็นทันที
- ถ้ารายงานว่าง ควรบอกวิธีปรับเงื่อนไขและปีที่เลือก

---

## S13: `v_view_student_courses.php`

### จุดประสงค์
- แสดงข้อมูลการลงทะเบียนของนักศึกษา
- แยกวิชาเป็นหมวดหลัก/เลือก/วิทยานิพนธ์/อื่น ๆ
- แสดงรายละเอียด course แบบอ่านอย่างเดียว

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| Column sorting / arrow | ใช้เรียงตารางตามลำดับที่กำหนด |
| Breadcrumb | ย้อนกลับไป curriculum หรือหน้าแรก |

### ขั้นตอนการใช้งาน
1. เปิดจาก curriculum หรือจากชื่อ student code ใน dashboard
2. ตรวจข้อมูลนักศึกษา
3. ดูตารางรายวิชาที่ลงทะเบียน
4. ถ้าต้องการดูรายละเอียดเพิ่มเติม ให้กลับไปหน้าก่อนหน้า

### ตารางที่เกี่ยวข้อง
- อ่าน `mdl_user_student`
- อ่าน `mdl_student_registered_course`
- อ่าน `mdl_student_registration_term`
- อ่าน `mdl_course_ep`
- อ่าน `mdl_cur_course`

### หมายเหตุสำคัญ
- หน้านี้เป็น read-only
- เหมาะใช้เป็นหลักฐานประกอบว่าทำไม student คนนี้ถึงถูกจัดอยู่ใน curriculum นี้

---

## S14: `v_view_student_knowledge.php`

### จุดประสงค์
- แสดงคะแนน Knowledge แบบรายคน
- แสดง P1-P5 และสถานะการผ่าน
- เปิดทางไปแก้ CE results

### ปุ่ม/ตัวควบคุมที่สำคัญ
| Control | ทำอะไร |
|---|---|
| `แก้ไข CE` / link ไป manage CE | เปิด `v_manage_ce_results.php` |
| Breadcrumb | ย้อนกลับไป Knowledge summary |

### ขั้นตอนการใช้งาน
1. เปิดจากหน้าสรุป Knowledge
2. ตรวจโปรไฟล์นักศึกษา
3. ดูคะแนนรวม P1-P5
4. ตรวจรายละเอียดรายวิชาที่ผ่าน
5. ถ้าต้องแก้ CE ให้ไปหน้าจัดการ CE

### ตารางที่เกี่ยวข้อง
- อ่าน `mdl_user_student`
- อ่าน `mdl_student_registered_course`
- อ่าน `mdl_comp_exam_results`
- อ่าน view `v_student_knowledge_scores_final`
- อ่าน view ที่เกี่ยวข้องกับ grade / passed credits

### หมายเหตุสำคัญ
- เป็นหน้า detail สำคัญที่สุดของฝั่ง Knowledge
- ถ้าต้องทำคู่มือเชิงปฏิบัติ ให้ใส่ตัวอย่างการอ่าน P1-P5 ด้วย

---

## หน้าจอรองที่ควรใส่ในภาคผนวก

หน้าต่อไปนี้ยังใช้จริง แต่เหมาะจะอธิบายในภาคผนวกหรือคู่มือเทคนิคมากกว่าคู่มือผู้ใช้หน้าแรก:

- `v_knowledge.php`
- `v_list_englishskills.php`
- `v_list_tasks_research.php`
- `v_manage_ce_results.php`
- `v_edit_student_nts.php`
- `v_edit_task.php`
- `v_edit_tasks_research.php`
- `v_edit_cur.php`
- `v_edit_cur250923.php`
- `v_edit_student_nts_250922S.php`
- `v_sync_data_management.php`
- `v_sync_student_dup_management.php`
- `v_student_sync_controller.php`
- `v_ajax_process_sync.php`
- `api/*`

## สิ่งที่ควรเพิ่มในฉบับจริง

- ภาพหน้าจอทุกหน้าหลัก
- ตัวอย่างค่าจริงของ `setid` และ `sid`
- ตัวอย่าง error message ที่ผู้ใช้เจอได้จริง
- section วิธีแก้ปัญหาเบื้องต้น
- section สิทธิ์ผู้ใช้และหน้าที่เปิดได้

## ลำดับถัดไปที่แนะนำ

1. เติมข้อมูลระดับ field ของแต่ละหน้าจอ
2. ทำตาราง relation/database dictionary แบบละเอียด
3. จัดหน้า ER / DFD final
4. แยกภาคผนวกของไฟล์ backup และ legacy copy
