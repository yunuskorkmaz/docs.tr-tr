---
title: 'İzlenecek Yol: MaskedTextBox Denetimiyle Çalışma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: bcca6c5f5481d351a39a4e71532cc0f006075128
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>İzlenecek Yol: MaskedTextBox Denetimiyle Çalışma
Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Başlatma <xref:System.Windows.Forms.MaskedTextBox> denetimi  
  
-   Kullanarak <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> bir karakter maskeye uymuyor olduğunda kullanıcıyı uyarmak için olay işleyicisi  
  
-   Bir türe atama <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> özelliği ve kullanarak <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> bunlar çalışırken yürütmek için değer türü için geçerli değilse, kullanıcıyı uyarmak için olay işleyicisi  
  
## <a name="creating-the-project-and-adding-a-control"></a>Proje oluşturma ve denetim ekleme  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>MaskedTextBox denetimi formunuza eklemek için  
  
1.  Yerleştirmek istediğiniz formu açın <xref:System.Windows.Forms.MaskedTextBox> denetim.  
  
2.  Sürükleme bir <xref:System.Windows.Forms.MaskedTextBox> gelen denetim **araç** formunuza.  
  
3.  Denetimin sağ tıklatın ve seçin **özellikleri**. İçinde **özellikleri** penceresinde, seçin **maskesi** özelliği ve tıklatın **...**  özellik adının yanındaki (üç nokta) düğmesi.  
  
4.  İçinde **giriş maskesi** iletişim kutusunda **kısa tarih** maske ve tıklayın **Tamam**.  
  
5.  İçinde **özellikleri** penceresi kümesi <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> özelliğine `true`. Bu özellik, kullanıcı giriş maskesi tanımını ihlal ediyor bir karakter girişiminde her zaman ses kısa bip sesi neden olur.  
  
 Maske özelliğini destekleyen karakterden oluşan bir özeti Açıklamalar bölümüne bakın <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.  
  
## <a name="alert-the-user-to-input-errors"></a>Hataları giriş kullanıcıya uyar  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>Balon ipucu reddedilen maskesi giriş Ekle  
  
1.  Geri dönüp **araç** ve ekleme bir <xref:System.Windows.Forms.ToolTip> formunuza.  
  
2.  İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> başlatır olay <xref:System.Windows.Forms.ToolTip> Giriş bir hata oluştuğunda. Balon ipucu beş saniyede veya kullanıcı bağlantıya tıkladığında kadar görünür kalır.  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>Kullanıcı geçersiz bir tür için uyar  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>Geçersiz veri türleri için balon ipucu ekleyin  
  
1.  Formun içinde <xref:System.Windows.Forms.Form.Load> olay işleyicisi atamak bir <xref:System.Type> nesnesini temsil eden <xref:System.DateTime> için yazın <xref:System.Windows.Forms.MaskedTextBox> denetimin <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> özelliği:  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2.  Bir olay işleyicisi ekleme <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> olay:  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [MaskedTextBox Denetimi](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)
