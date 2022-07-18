# temel_dosyalama_odev

#küçük harfe çevrilmesi
with open('istanbul_data.txt', 'r+') as select:
    low_ch = select.read().lower()
    
#noktalama işaretlerinin kaldırılması
with open('istanbul_data.txt', 'r+') as f1:
    line1 = f1.readlines()
    for i in line1:
        if i in [".,:;!'-•*=%&/()?_"]:
            line1.pop(i)
            
#sadece sayıdan oluşan satırın yeni dosyaya eklenmemesi
with open('istanbul_data.txt', 'r+') as f2:
    line2 = f2.readlines()
    for i in line2:
        if i.isdigit() == True:
            line2.remove(i)
            
#unique satırlar oluşturulması
unique = list(set(open('istanbul_data.txt', 'r+').readlines()))

#türkçe harflerin replace edilmesi
with open('istanbul_data.txt', 'r+') as f3:
    line3 = f3.readlines()
    replace_dic= {'ş':'s','ğ':'g','ü':'u', 'ö':'o', 'ç':'c', 'ı':'i'}
    replace_str=''
    for i in range(len(line3)):
        lines = line3[i]
        for chr in range(len(lines)):
            if lines[chr] in replace_dic:
                replace_str += replace_dic[lines[chr]]
            else:
                replace_str += lines[chr]
print(line3)
