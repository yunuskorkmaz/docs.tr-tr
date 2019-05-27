---
title: 'Nasıl yapılır: ColorDialog Bileşeni ile Renk Paleti Gösterme'
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
ms.openlocfilehash: ff29df4ecfc90eabe8e3be0e5a6a126858799c16
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053417"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>Nasıl yapılır: ColorDialog Bileşeni ile Renk Paleti Gösterme
[ColorDialog](colordialog-component-windows-forms.md) bileşeni bir renk paletini görüntüler ve kullanıcının seçtiği bir renk içeren bir özelliğini döndürür.  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>ColorDialog bileşeni kullanarak bir renk seçmek için  
  
1. İletişim kutusunu kullanarak görüntüleme <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.  
  
2. Kullanım <xref:System.Windows.Forms.DialogResult> özelliği iletişim kutusu nasıl kapatıldığı belirler.  
  
3. Kullanım <xref:System.Windows.Forms.ColorDialog.Color%2A> özelliği <xref:System.Windows.Forms.ColorDialog> seçilen rengini ayarlamak için bileşen.  
  
     Aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi açılır bir <xref:System.Windows.Forms.ColorDialog> bileşeni. Bir renk seçilen ve kullanıcı olduğunda tıkladığında **Tamam**, <xref:System.Windows.Forms.Button> denetimin arka plan rengi seçilen renge ayarlayın. Formunuza sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetimi ve bir <xref:System.Windows.Forms.ColorDialog> bileşeni.  
  
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
  
     (Visual C#, Visual C++) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.  
  
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
