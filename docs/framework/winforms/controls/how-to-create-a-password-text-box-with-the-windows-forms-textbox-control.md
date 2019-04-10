---
title: 'Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: ab5df1233c16a7ce076efa817fb14808b588ebcd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300989"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma
Bir kullanıcı bir dize türleri, yer tutucu karakterleri görüntüler bir Windows Forms metin kutusuna bir parola kutusudur.  
  
### <a name="to-create-a-password-text-box"></a>Parola metin kutusu oluşturma  
  
1. Ayarlama <xref:System.Windows.Forms.TextBox.PasswordChar%2A> özelliği <xref:System.Windows.Forms.TextBox> belirli bir karakterin denetime.  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Özellik metin kutusunda görüntülenen karakter belirtir. Örneğin, yıldız işareti (parola) kutusunda görüntülenen istiyorsanız belirtin * için <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Özellikler penceresindeki özellik. Ardından, metin kutusuna bir kullanıcı türleri, hangi karakter bağımsız olarak bir yıldız işareti görüntülenir.  
  
2. (İsteğe bağlı) Ayarlama <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> özelliği. Özellik karakterlerinin kaçının tutulacağını metin kutusuna yazılabilir belirler. En fazla uzunluk aşıldığında, sistem bir bip sesi yayar ve metin kutusunda daha fazla tüm karakterleri kabul etmez. Bu bir parola uzunluğu en fazla yapmak isteyebilirsiniz Not, parolanızı tahmin etmeye çalıştığınız saldırganlar için kullanışlı olabilir.  
  
     Aşağıdaki kod örneğinde nasıl başlatılacağını en fazla 14 karakter uzunluğunda bir dize kabul edin ve dize yerine bir yıldız görüntüler bir metin kutusu gösterir. `InitializeMyControl` Yordamı değil yürütülecek otomatik olarak; çağrılması gerekir.  
  
    > [!IMPORTANT]
    >  Kullanarak <xref:System.Windows.Forms.TextBox.PasswordChar%2A> özellik metin kutusundaki diğer kişilerin bunlar, girerek kullanıcı gözlemlerseniz, bir kullanıcının parolasını belirlemek mümkün olmayacaktır olun yardımcı olabilir. Bu güvenlik önlemi depolama veya uygulama mantığınızın nedeniyle gerçekleşen parola iletim tamamını kapsamaz. Girilen metin herhangi bir yolla şifrelenmediğinden diğer gizli verileri gibi düşünmelisiniz. Bu nedenle görünmez olsa da, (bazı ek güvenlik önlemi uygulanmış sürece) parola yine de bir düz metin dizesi olarak kabul ediliyor.  
  
    ```vb  
    Private Sub InitializeMyControl()  
       ' Set to no text.  
       TextBox1.Text = ""  
       ' The password character is an asterisk.  
       TextBox1.PasswordChar = "*"  
       ' The control will allow no more than 14 characters.  
       TextBox1.MaxLength = 14  
    End Sub  
    ```  
  
    ```csharp  
    private void InitializeMyControl()  
    {  
       // Set to no text.  
       textBox1.Text = "";  
       // The password character is an asterisk.  
       textBox1.PasswordChar = '*';  
       // The control will allow no more than 14 characters.  
       textBox1.MaxLength = 14;  
    }  
    ```  
  
    ```cpp  
    private:  
       void InitializeMyControl()  
       {  
          // Set to no text.  
          textBox1->Text = "";  
          // The password character is an asterisk.  
          textBox1->PasswordChar = '*';  
          // The control will allow no more than 14 characters.  
          textBox1->MaxLength = 14;  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- [TextBox Denetimine Genel Bakış](textbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma](how-to-create-a-read-only-text-box-windows-forms.md)
- [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
