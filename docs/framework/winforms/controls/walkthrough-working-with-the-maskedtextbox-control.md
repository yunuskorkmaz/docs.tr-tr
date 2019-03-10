---
title: 'İzlenecek yol: MaskedTextBox denetimiyle çalışma'
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
ms.openlocfilehash: 9633f2f871d08b70d6286f510a9ba5cac78ae529
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703094"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>İzlenecek yol: MaskedTextBox denetimiyle çalışma
Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Başlatma <xref:System.Windows.Forms.MaskedTextBox> denetimi  
  
-   Kullanarak <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> bir karakterin maskesini uymuyor olduğunda kullanıcıyı uyarmak için olay işleyicisi  
  
-   Bir türe atama <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> özelliği ve kullanarak <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> bunlar çalışırken yürütmek için değer türü için geçerli değilse, kullanıcıyı uyarmak için olay işleyicisi  
  
## <a name="creating-the-project-and-adding-a-control"></a>Proje oluşturma ve denetim ekleme  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>MaskedTextBox denetimi formunuza eklemek için  
  
1.  Form üzerinde yerleştirmek istediğiniz açın <xref:System.Windows.Forms.MaskedTextBox> denetimi.  
  
2.  Sürükleme bir <xref:System.Windows.Forms.MaskedTextBox> denetimi **araç kutusu** formunuza.  
  
3.  Denetime sağ tıklayın ve seçin **özellikleri**. İçinde **özellikleri** penceresinde **maskesi** özelliği ve tıklatın **...**  özellik adının yanındaki (üç nokta) düğmesi.  
  
4.  İçinde **giriş maskesi** iletişim kutusunda **kısa tarih** maske ve tıklayın **Tamam**.  
  
5.  İçinde **özellikleri** penceresi kümesi <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> özelliğini `true`. Bu özellik, kullanıcı giriş maskesi tanımını ihlal eden bir karakter girişiminde her zaman ses kısa bir bip sesi neden olur.  
  
 Maske özelliği destekleyen karakterleri özeti için Açıklamalar bölümüne bakın. <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.  
  
## <a name="alert-the-user-to-input-errors"></a>Kullanıcı girişi hataları için uyarı  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>Reddedilen maskesi girişi için bir balon ipucunu ekleyin  
  
1.  Geri dönüp **araç kutusu** ve ekleme bir <xref:System.Windows.Forms.ToolTip> formunuza.  
  
2.  İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> oluşturan olay <xref:System.Windows.Forms.ToolTip> Giriş bir hata oluştuğunda. Balon ipucu veya beş saniye kadar kullanıcı buna tıkladığında görünür kalır.  
  
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
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>Kullanıcı, geçerli olmayan bir tür için uyarı  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>Geçersiz veri türleri için bir balon ipucunu ekleyin  
  
1.  Formun içinde <xref:System.Windows.Forms.Form.Load> olay işleyicisi, Ata bir <xref:System.Type> nesnesini temsil eden <xref:System.DateTime> için yazın <xref:System.Windows.Forms.MaskedTextBox> denetimin <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> özelliği:  
  
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
  
2.  İçin bir olay işleyicisi ekleme <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> olay:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.MaskedTextBox>
- [MaskedTextBox Denetimi](maskedtextbox-control-windows-forms.md)
