---
title: TextBox denetimiyle parola metin kutusu oluşturma
description: Bir Kullanıcı bir dize yazdığında, yer tutucu karakterleri görüntüleyen Windows Forms bir metni nasıl oluşturabileceğinizi öğrenin.
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
ms.openlocfilehash: 6d7e61eefa44ce3152aa77e3922bde471a4aeaf3
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904318"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma

Parola kutusu, bir Kullanıcı bir dize yazdığında yer tutucu karakterleri görüntüleyen bir Windows Forms metin kutusudur.

### <a name="to-create-a-password-text-box"></a>Parola metin kutusu oluşturmak için

1. <xref:System.Windows.Forms.TextBox.PasswordChar%2A> <xref:System.Windows.Forms.TextBox> Denetimin özelliğini belirli bir karakter olarak ayarlayın.

    <xref:System.Windows.Forms.TextBox.PasswordChar%2A>Özelliği metin kutusunda gösterilecek karakteri belirtir. Örneğin, parola kutusunda yıldız işaretlerini isterseniz, Özellikler penceresi özellik için * belirtin <xref:System.Windows.Forms.TextBox.PasswordChar%2A> . Ardından, kullanıcının metin kutusunda ne kadar karakterinde olduğuna bakılmaksızın bir yıldız işareti görüntülenir.

2. Seçim Özelliği ayarlayın <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> . Özelliği, metin kutusuna kaç karakter girilebileceğini belirler. Maksimum uzunluk aşılırsa sistem bir bip sesi yayar ve metin kutusu daha fazla karakter kabul etmez. Parolayı tahmin etmeye çalışan saldırganlar için bir parolanın en fazla uzunluğu kullanım dışı olabileceğinden bunu yapmak istemediğiniz unutulmamalıdır.

    Aşağıdaki kod örneğinde, en fazla 14 karakter uzunluğunda bir dizeyi kabul edecek ve dize yerine yıldız işaretlerini gösteren bir metin kutusunun nasıl başlatıldığı gösterilmektedir. `InitializeMyControl`Yordam otomatik olarak yürütülmeyecektir; çağrılmalıdır.

    > [!IMPORTANT]
    > <xref:System.Windows.Forms.TextBox.PasswordChar%2A>Özelliği metin kutusu üzerinde kullanmak, Kullanıcı tarafından giriş gözlemlerse, diğer kişilerin bir kullanıcının parolasını belirleyememesini sağlamaya yardımcı olabilir. Bu güvenlik ölçüsü, Uygulama mantığınız nedeniyle gerçekleşebileceğini herhangi bir depolama veya parola aktarımını kapsamaz. Girilen metin herhangi bir şekilde şifrelenmediğinden, diğer gizli veriler gibi davranmanız gerekir. Bu gibi görünmese de, parola hala düz metin dizesi olarak değerlendirildi (bazı ek güvenlik ölçüsü gerçekleştirmediğiniz sürece).

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
