---
title: TextBox denetimiyle parola metin kutusu oluşturma
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
ms.openlocfilehash: ff4706a736d15f14cf437c808219e9088773dc6d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731289"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma

Parola kutusu, bir Kullanıcı bir dize yazdığında yer tutucu karakterleri görüntüleyen bir Windows Forms metin kutusudur.

### <a name="to-create-a-password-text-box"></a>Parola metin kutusu oluşturmak için

1. <xref:System.Windows.Forms.TextBox> denetiminin <xref:System.Windows.Forms.TextBox.PasswordChar%2A> özelliğini belirli bir karakter olarak ayarlayın.

    <xref:System.Windows.Forms.TextBox.PasswordChar%2A> özelliği metin kutusunda gösterilecek karakteri belirtir. Örneğin, parola kutusunda yıldız işaretlerini isterseniz, Özellikler penceresi <xref:System.Windows.Forms.TextBox.PasswordChar%2A> özelliği için * belirtin. Ardından, kullanıcının metin kutusunda ne kadar karakterinde olduğuna bakılmaksızın bir yıldız işareti görüntülenir.

2. Seçim <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> özelliğini ayarlayın. Özelliği, metin kutusuna kaç karakter girilebileceğini belirler. Maksimum uzunluk aşılırsa sistem bir bip sesi yayar ve metin kutusu daha fazla karakter kabul etmez. Parolayı tahmin etmeye çalışan saldırganlar için bir parolanın en fazla uzunluğu kullanım dışı olabileceğinden bunu yapmak istemediğiniz unutulmamalıdır.

    Aşağıdaki kod örneğinde, en fazla 14 karakter uzunluğunda bir dizeyi kabul edecek ve dize yerine yıldız işaretlerini gösteren bir metin kutusunun nasıl başlatıldığı gösterilmektedir. `InitializeMyControl` yordamı otomatik olarak yürütülmez; çağrılması gerekir.

    > [!IMPORTANT]
    > Metin kutusu üzerinde <xref:System.Windows.Forms.TextBox.PasswordChar%2A> özelliğini kullanmak, Kullanıcı tarafından giriş gözlemlerse, diğer kişilerin bir kullanıcının parolasını belirleyememesini sağlamaya yardımcı olabilir. Bu güvenlik ölçüsü, Uygulama mantığınız nedeniyle gerçekleşebileceğini herhangi bir depolama veya parola aktarımını kapsamaz. Girilen metin herhangi bir şekilde şifrelenmediğinden, diğer gizli veriler gibi davranmanız gerekir. Bu gibi görünmese de, parola hala düz metin dizesi olarak değerlendirildi (bazı ek güvenlik ölçüsü gerçekleştirmediğiniz sürece).

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
