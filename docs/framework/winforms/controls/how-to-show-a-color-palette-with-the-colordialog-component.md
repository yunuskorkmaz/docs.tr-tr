---
title: 'Nasıl Yapılır: ColorDialog Bileşeni ile Renk Paleti Gösterme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
ms.openlocfilehash: 0406ef7a32678bd149c0024348a7adf1f0b72926
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141789"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>Nasıl Yapılır: ColorDialog Bileşeni ile Renk Paleti Gösterme
[ColorDialog](colordialog-component-windows-forms.md) bileşeni bir renk paleti görüntüler ve kullanıcının seçtiği rengi içeren bir özellik döndürür.  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>ColorDialog bileşenini kullanarak bir renk seçmek için  
  
1. Yöntemi kullanarak iletişim kutusunu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> görüntüleyin.  
  
2. İletişim <xref:System.Windows.Forms.DialogResult> kutusunun nasıl kapatıldığını belirlemek için özelliği kullanın.  
  
3. Seçilen <xref:System.Windows.Forms.ColorDialog.Color%2A> rengi ayarlamak <xref:System.Windows.Forms.ColorDialog> için bileşenin özelliğini kullanın.  
  
     Aşağıdaki örnekte, <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi bir <xref:System.Windows.Forms.ColorDialog> bileşeni açar. Bir renk seçildiğinde ve kullanıcı **Tamam'ı**tıklattığında, denetimin <xref:System.Windows.Forms.Button> arka plan rengi seçilen renge ayarlanır. Örnek, formunuzun bir <xref:System.Windows.Forms.Button> denetimi <xref:System.Windows.Forms.ColorDialog> ve bileşeni olduğunu varsayar.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     (Görsel C#, Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog Bileşeni](colordialog-component-windows-forms.md)
