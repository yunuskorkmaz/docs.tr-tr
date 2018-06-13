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
ms.openlocfilehash: 41bfb2bc1a1ead5bb289264c44145b88721efe49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534306"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma
Parola kutusu yer tutucu karakterler bir kullanıcı bir dize türleri sırada görüntüleyen bir Windows Forms metin kutusu olur.  
  
### <a name="to-create-a-password-text-box"></a>Parola metin kutusu oluşturmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.TextBox.PasswordChar%2A> özelliği <xref:System.Windows.Forms.TextBox> denetlemek için bir özel karakter.  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Özellik metin kutusunda görüntülenen karakter belirtir. Örneğin, parola kutusunda görüntülenen yıldızlar istiyorsanız belirtin * için <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Özellikleri penceresinde özelliği. Ardından, metin kutusuna bir kullanıcı türleri hangi karakter bağımsız olarak bir yıldız işareti görüntülenir.  
  
2.  (İsteğe bağlı) Ayarlama <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> özelliği. Özelliği kaç karakterin metin kutusunda girilebilen belirler. En büyük uzunluğu aştı, sistem bip sesi yayar ve metin kutusuna daha fazla tüm karakterleri kabul etmez. Bu parola uzunluk üst sınırı yapmak isteyebilirsiniz Not kullanım için parolanızı tahmin etmeyi denemelerini saldırganlar olabilir.  
  
     Aşağıdaki kod örneği, en çok 14 karakter uzunluğunda bir dize kabul etmek ve dize yerine bir yıldız işareti görüntüleme bir metin kutusu başlatılmaya gösterilmektedir. `InitializeMyControl` Yordamı değil yürütülecek otomatik olarak; çağrılması gerekir.  
  
    > [!IMPORTANT]
    >  Kullanarak <xref:System.Windows.Forms.TextBox.PasswordChar%2A> bir metin kutusu özellikte diğer kişilerin bunu giren kullanıcı gözlemlerseniz, bir kullanıcının parolasını belirlemek mümkün olmaz olun yardımcı olabilir. Bu güvenlik önlemi her tür depolama ya da uygulama mantığınızın nedeniyle oluşabilir parola iletimini kapsamaz. Girilen metin herhangi bir şekilde şifrelenmediğinden diğer gizli veriler gibi düşünmelisiniz. Bu nedenle görünmez olsa bile (bazı ek güvenlik önlemi uygulanan sürece) parola hala bir düz metin dizesi olarak kabul ediliyor.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox Denetimi](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
