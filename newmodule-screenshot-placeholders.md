# Newmodule Screenshot Placeholders

Last updated: 2026-07-27

Use these placeholders when you paste screenshots into the final manual.

## Placeholder Format

Recommended text to insert in the manual:

```md
{{IMG: SCREEN_ID | short caption}}
```

Example:

```md
{{IMG: S01 | หน้าแรก / Dashboard หลัก}}
```

## Screenshot Checklist

| ID | File | Suggested caption | Where to place in manual | Screenshot notes |
|---|---|---|---|---|
| S01 | `v_index.php` | หน้าแรก / Dashboard หลัก | ก่อน section หน้าแรก | แคปให้เห็น dropdown หลักสูตรและทางลัดหลัก |
| S02 | `v_curriculum_management.php` | หน้าจัดการหลักสูตร | ก่อน section จัดการหลักสูตร | ให้เห็นปุ่มไป student, sync, course |
| S03 | `v_manage_cur_course.php` | จัดการรายวิชาในโครงสร้างหลักสูตร | ก่อน section รายวิชาในหลักสูตร | ให้เห็น lock status และปุ่มบันทึก |
| S04 | `v_manage_cur_student.php` | จัดการนักศึกษาในหลักสูตร | ก่อน section จัดการนักศึกษา | ให้เห็นตารางรายชื่อนักศึกษาและ checkbox |
| S05 | `v_manage_cur_student_detail.php` | แก้ไขข้อมูลนักศึกษา | ก่อน section รายละเอียดนักศึกษา | ให้เห็นฟอร์มแก้ข้อมูลและส่วน registration summary |
| S06 | `v_softskills.php` | SoftSkills Dashboard | ก่อน section SoftSkills dashboard | ให้เห็นกราฟ/summary และลิงก์จัดการรายคน |
| S07 | `v_manage_softskills.php` | บันทึก Soft Skills และ English Scores | ก่อน section บันทึกคะแนน | ให้เห็นฟอร์ม soft skills และฟอร์ม English แยกกันชัดเจน |
| S08 | `v_nts.php` | NTS Dashboard | ก่อน section NTS dashboard | ให้เห็นช่องค้นหาและตาราง summary |
| S09 | `v_view_student_nts.php` | รายละเอียด NTS รายคน | ก่อน section detail NTS | ให้เห็นข้อมูลโปรไฟล์และตาราง NTS รายวิชา/กิจกรรม |
| S10 | `v_research.php` | Research Dashboard | ก่อน section Research dashboard | ให้เห็นรายการนักศึกษาและทางไปจัดการ task |
| S11 | `v_view_student_research.php` | รายละเอียด Task และ Alert รายคน | ก่อน section detail Research | ให้เห็นตาราง task และ alert |
| S12 | `v_view_report.php` | หน้าสร้างรายงาน | ก่อน section report | ให้เห็น filter และปุ่ม export CSV |
| S13 | `v_view_student_courses.php` | รายละเอียดการลงทะเบียนนักศึกษา | ก่อน section student courses | ให้เห็น breadcrumb และตารางวิชาแบ่งหมวด |
| S14 | `v_view_student_knowledge.php` | รายละเอียดคะแนน Knowledge | ก่อน section knowledge detail | ให้เห็น P1-P5 และสถานะผ่าน/ไม่ผ่าน |

## Optional Extra Screens

If you want a more complete manual, add these too:

| ID | File | Suggested caption | Why include it |
|---|---|---|---|
| O01 | `v_knowledge.php` | Knowledge Dashboard | Helps explain the route to student knowledge details |
| O02 | `v_list_englishskills.php` | English skills list | Shows the English setup entry point |
| O03 | `v_list_tasks_research.php` | Research task list | Shows task master maintenance |
| O04 | `v_manage_ce_results.php` | Manage CE results | Useful for Knowledge flow and CE explanation |
| O05 | `v_edit_student_nts.php` | Edit student NTS | Useful for the NTS edit workflow |
| O06 | `v_edit_task.php` | Edit research task | Useful for task master workflow |
| O07 | `v_edit_cur.php` | Edit curriculum | Useful for curriculum master workflow |
| O08 | `v_sync_data_management.php` | Sync management | Useful for duplicate / sync procedures |

## Copy-Paste Placeholder Blocks

You can paste these blocks into the manual:

### Home

```md
{{IMG: S01 | หน้าแรก / Dashboard หลัก}}
```

### Curriculum Hub

```md
{{IMG: S02 | หน้าจัดการหลักสูตร}}
```

### Course Setup

```md
{{IMG: S03 | จัดการรายวิชาในโครงสร้างหลักสูตร}}
```

### Student Setup

```md
{{IMG: S04 | จัดการนักศึกษาในหลักสูตร}}
```

### Student Detail

```md
{{IMG: S05 | แก้ไขข้อมูลนักศึกษา}}
```

### SoftSkills

```md
{{IMG: S06 | SoftSkills Dashboard}}
```

```md
{{IMG: S07 | บันทึก Soft Skills และ English Scores}}
```

### NTS

```md
{{IMG: S08 | NTS Dashboard}}
```

```md
{{IMG: S09 | รายละเอียด NTS รายคน}}
```

### Research

```md
{{IMG: S10 | Research Dashboard}}
```

```md
{{IMG: S11 | รายละเอียด Task และ Alert รายคน}}
```

### Report

```md
{{IMG: S12 | หน้าสร้างรายงาน}}
```

### Student Detail Views

```md
{{IMG: S13 | รายละเอียดการลงทะเบียนนักศึกษา}}
```

```md
{{IMG: S14 | รายละเอียดคะแนน Knowledge}}
```

## Suggested Capture Order

1. S01
2. S02
3. S03
4. S04
5. S05
6. S06
7. S07
8. S08
9. S09
10. S10
11. S11
12. S12
13. S13
14. S14

## Quick Rules for Capture

- Capture the full visible browser area, not only the table.
- Keep the breadcrumb and page title visible when possible.
- If a page has a long table, one top screenshot is enough unless the table structure needs explanation.
- If the page has an important button or lock state, make sure the button is visible in the shot.
- Use one screenshot per screen unless the workflow is split into clearly different states.
