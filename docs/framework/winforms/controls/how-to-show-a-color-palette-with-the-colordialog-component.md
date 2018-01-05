---
title: "Nasıl Yapılır: ColorDialog Bileşeni ile Renk Paleti Gösterme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8abaab09d2c2e20211463bb8fc93d7efaa1b38fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>Nasıl Yapılır: ColorDialog Bileşeni ile Renk Paleti Gösterme
[ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md) bileşen renk paletini görüntüler ve kullanıcının seçildi renk içeren bir özellik döndürür.  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>ColorDialog bileşeni kullanarak bir renk seçmek için  
  
1.  İletişim kutusunu kullanarak görüntüleme <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.  
  
2.  Kullanım <xref:System.Windows.Forms.DialogResult> iletişim kutusunun nasıl kapatıldığını belirlemek için özellik.  
  
3.  Kullanım <xref:System.Windows.Forms.ColorDialog.Color%2A> özelliği <xref:System.Windows.Forms.ColorDialog> seçilen rengini ayarlamak için bileşen.  
  
     Aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi açılır bir <xref:System.Windows.Forms.ColorDialog> bileşeni. Bir renk seçilen ve kullanıcı olduğunda tıklar **Tamam**, <xref:System.Windows.Forms.Button> denetimin arka plan rengi, seçilen renk ayarlanır. Formunuz sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetim ve <xref:System.Windows.Forms.ColorDialog> bileşeni.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog Bileşeni](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)
