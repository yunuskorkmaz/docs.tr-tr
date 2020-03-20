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
ms.openlocfilehash: db32b3ec88a07747ea3e286af9f04edce3f1ba3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182067"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>İzlenecek Yol: MaskedTextBox Denetimiyle Çalışma
Bu gözden geçirmede gösterilen görevler şunlardır:  
  
- <xref:System.Windows.Forms.MaskedTextBox> Denetimi başlatma  
  
- Bir <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> karakter maskeye uymadığında kullanıcıyı uyarmak için olay işleyicisini kullanma  
  
- <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> Bir tür özelliği atama ve <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> işlemeye çalıştıkları değer türü için geçerli olmadığında kullanıcıyı uyarmak için olay işleyicisini kullanma  
  
## <a name="creating-the-project-and-adding-a-control"></a>Proje Oluşturma ve Denetim Ekleme  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>Formunuza MaskeliTextBox denetimi eklemek için  
  
1. <xref:System.Windows.Forms.MaskedTextBox> Denetimi yerleştirmek istediğiniz formu açın.  
  
2. Denetimi <xref:System.Windows.Forms.MaskedTextBox> Araç **Kutusu'ndan** formunuza sürükleyin.  
  
3. Denetimi sağ tıklatın ve **Özellikler'i**seçin. **Özellikler** penceresinde Maske **özelliğini** seçin ve özellik adının yanındaki **...** (elips) düğmesini tıklatın.  
  
4. Giriş **Maskesi** iletişim kutusunda, Kısa **Tarih** maskesini seçin ve **Tamam'ı**tıklatın.  
  
5. **Özellikler** penceresinde <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> özelliği `true`' ye göre ayarlar. Bu özellik, kullanıcı maske tanımını ihlal eden bir karakter girişi yapmaya çalıştığında kısa bir bip sesine neden olur.  
  
 Maske özelliğinin desteklediği karakterlerin özeti için özelliğin Açıklamalar bölümüne <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> bakın.  
  
## <a name="alert-the-user-to-input-errors"></a>Kullanıcıyı Giriş Hataları Konusunda Uyar  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>Reddedilen maske girişi için balon ucu ekleme  
  
1. **Araç Kutusuna** dönün ve <xref:System.Windows.Forms.ToolTip> formunuza bir ekleme.  
  
2. Bir giriş hatası <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> <xref:System.Windows.Forms.ToolTip> oluştuğunda yükselten olay için bir olay işleyicisi oluşturun. Balon ucu beş saniye veya kullanıcı onu tıklayana kadar görünür kalır.  
  
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
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>Kullanıcıyı Geçerli Olmayan Bir Tür e karşı uyar  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>Geçersiz veri türleri için balon ucu ekleme  
  
1. Formunuzun olay <xref:System.Windows.Forms.Form.Load> <xref:System.Type> işleyicisinde, denetimin <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> özelliğine <xref:System.DateTime> <xref:System.Windows.Forms.MaskedTextBox> türü temsil eden bir nesne atayın:  
  
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
  
2. Olay için bir olay <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> işleyicisi ekleyin:  
  
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
