# Doanlaptrinh01
Nhập thông tin sinh viên và in ra bảng điểm cuối kỳ

# Hàm nhập thông tin sinh viên
def NhapDauVao():
    def HoTen():
        while True:
            n = input("Nhập tên: ")
            m = n.split(' ') # Tách chuỗi ra thành các chuỗi nhỏ trong mảng
            if(2<=len(m)<=6):
                for i in range(len(m)): # Chạy thứ tự các thành phần trong mảng
                    if(len(m[i])<=8): # Xét điều kiện mỗi chữ không quá 8 ký tự
                        if(m[i].isdigit() or not m[i].isalpha()): # Xét điều kiện mỗi chữ có phải là số hay ký tự không ?
                            print("-Tên bạn nhập không hợp lệ-")
                            print("---Vui lòng nhập lại---")
                            break # Nếu có chữ là số thì phá vòng lặp quay lại phần nhập
                    else:
                        print("-Tên bạn nhập không hợp lệ-")
                        print("---Vui lòng nhập lại---")
                        break # Nếu chữ quá 8 ký tự thì phá vòng lặp quay lại phần nhập
                else: 
                    hoten = ' '.join(m) # Hàm join và xuất ra Họ tên  
                    return f"\nHọ và tên: {hoten}"
                    break # Nếu tất cả là chuỗi và không có chuỗi nào quá 8 kí tự thì phá khỏi vòng while
            else:
                print("-Tên bạn nhập không hợp lệ-")
                print("---Vui lòng nhập lại---")
                continue 
    # Module canlendar và hàm isleap(year)
    import calendar
    from datetime import date
    def NTNS():
        while True:
            #Tạo vòng lặp để nhập năm
            nam = input("Năm sinh: ")
            if(nam.isdigit()):
                if(int(nam) not in range(1000,10000)): # Xét điều kiện xem số năm có phải là số có 4 chữ số hay không ?
                    print("\n-Năm sinh không hợp lệ-")
                    print("---Vui lòng nhập lại---")
                    continue
                else:
                    today = date.today()
                    year_today = today.year
                    if ((year_today - int(nam)) < 18): # Điều kiện để đủ tuổi nhập học đại học
                        print("\n-Chưa đủ tuổi học đại học-")
                        print("---Vui lòng nhập lại---")
                        continue
                    else:
                        break
            else:
                print("\n-Năm sinh không hợp lệ-")
                print("---Vui lòng nhập lại---")
                continue
        #Tạo vòng lặp để nhập tháng        
        while True:   
            thang = input("Tháng: ") 
            if(thang.isdigit()):
                if(int(thang) not in range(1,13)): # Điều kiện để nhập tháng
                    print("\n-Rất tiếc! Tháng này không tồn tại-")
                    print("---Vui lòng nhập lại---")
                    continue
                else:
                    break
            else:
                print("\n-Rất tiếc! Tháng này không tồn tại-")
                print("---Vui lòng nhập lại---")
                continue

        # Tạo vòng lặp để nhập ngày
        while True:
            ngay = input("Ngày sinh: ") 
            if(ngay.isdigit()):
                if(int(ngay) not in range(1, 32)):# Điều kiện để nhập ngày
                    print("\n-Ngày này không tồn tại-")
                    print("---Vui lòng nhập lại---")
                    continue
                else:
                    #Tạo biến những tháng có 30 ngày và tháng có 31 ngày
                    thang_31 = (1,3,5,7,8,10,12)
                    thang_30 = (2,4,6,9,11)
                    if(int(thang) in thang_31):
                        if(calendar.isleap(int(nam))): # Hàm isleap để kiểm tra năm nhuận
                            if(int(thang) == 2 and int(ngay) > 29 or int(ngay) > 31): # Năm nhuận
                                print("\n-Ngày này không tồn tại-")
                                print("---Vui lòng nhập lại---")
                                continue
                            else:    
                                return f"Ngày sinh: {ngay + '/' + thang + '/' + nam}"
                                break 
                        else:
                            if(int(thang)==2 and int(ngay) > 28): # năm không nhuận
                                print("\n-Ngày này không tồn tại-")
                                print("---Vui lòng nhập lại---")
                                continue
                            else: # Trả giá trị về ngày tháng năm sinh theo hệ str
                                return f"Ngày sinh: {ngay + '/' + thang + '/' + nam}"  
                                break
                    elif(int(thang) in thang_30):
                        if(calendar.isleap(int(nam))): # Hàm isleap để kiểm tra năm nhuận
                            if(int(thang) == 2 and int(ngay) > 29 or int(ngay) > 30): # Năm nhuận
                                print("\n-Ngày này không tồn tại-")
                                print("---Vui lòng nhập lại---")
                                continue
                            else:    
                                return f"Ngày sinh: {ngay + '/' + thang + '/' + nam}"
                                break
                        else:
                            if(int(thang)==2 and int(ngay) > 28): # năm không nhuận
                                print("\n-Ngày này không tồn tại-")
                                print("---Vui lòng nhập lại---")
                                continue
                            else: # Trả giá trị về ngày tháng năm sinh theo hệ str
                                return f"Ngày sinh: {ngay + '/' + thang + '/' + nam}"  
                                break
                    else:
                        print("\n-Ngày này không tồn tại-")
                        print("---Vui lòng nhập lại---")
                        continue       
            else:
                print("\n-Ngày này không tồn tại-")
                print("---Vui lòng nhập lại---")
                continue
    # Hàm in ra MSSV
    def MSSV():
        while True:
            mssv = input("Nhập mã số sinh viên: ") # Nhập mã số sinh viên
            if(not mssv.isdigit() or len(mssv) != 10): # điều kiện khi nhập mã số sinh viên
                print("\n-Mã số sinh viên không hợp lệ-")
                print("---Vui lòng nhập lại---")
                continue
            else:
                return f"MSSV: {mssv}" # Trả về gia trị mssv
                break
    return HoTen() + '\n' + NTNS() + '\n' + MSSV() # Trả về giá trị của 3 hàm trên


#Nhập thông tin sinh viên
print("---Mời nhập thông tin của sinh viên---")
sv = NhapDauVao()   
