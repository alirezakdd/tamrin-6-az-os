## چالش ۱: هندسه در ترمینال

### کد (`rectangle.sh`)

```bash
#!/bin/bash

read -p "طول مستطیل رو وارد کنید: " length
read -p "عرض مستطیل رو وارد کنید: " width

# بررسی درست بودن ورودی‌ ها
if ! [[ "$length" =~ ^[0-9]+$ && "$width" =~ ^[0-9]+$ ]] ||
   (( length <= 0 || width <= 0 )); then
    echo "خطا: طول و عرض باید عدد صحیح مثبت باشند."
    exit 1
fi

area=$((length * width))
perimeter=$((2 * (length + width)))

echo "مساحت مستطیل: $area"
echo "محیط مستطیل: $perimeter"
```


### execution

```bash
chmod +x rectangle.sh
./rectangle.sh
```


---
## چالش ۲: کارآگاه ترمینال (بررسی وجود کاربر)

### کد (`check_user.sh`)

```bash
#!/bin/bash

# بررسی تعداد آرگومان‌ های ورودی
if [ "$#" -ne 1 ]; then
    echo "نحوه استفاده: $0 username"
    exit 1
fi

username="$1"

# جست‌وجوی نام کاربر در فایل passwd
if grep -q "^${username}:" /etc/passwd; then
    echo "کاربر '$username' در سیستم وجود دارد."
else
    echo "کاربر '$username' در سیستم وجود ندارد."
fi
```
.

### execution

```bash
chmod +x check_user.sh
./check_user.sh alireza
```

### نمونه خروجی

در صورت وجود کاربر:

```text
کاربر 'alireza' در سیستم وجود دارد.
```

در صورت عدم وجود کاربر:

```text
کاربر 'unknownuser' در سیستم وجود ندارد.
```

در صورت وارد نکردن نام کاربر:

```text
نحوه استفاده: ./check_user.sh username
```

---
