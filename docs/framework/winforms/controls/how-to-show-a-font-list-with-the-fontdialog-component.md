---
title: "Nasıl Yapılır: FontDialog Bileşeni ile Yazı Tipi Listesi Gösterme"
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
- fonts [Windows Forms], showing list
- FontDialog component [Windows Forms]
- fonts [Windows Forms], attributes
- Font property [Windows Forms], setting with FontDialog component
- Font dialog box [Windows Forms], displaying
- fonts [Windows Forms], selecting
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd04a44e6f6e3df26a643a8937e20e232e7471a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a>Nasıl Yapılır: FontDialog Bileşeni ile Yazı Tipi Listesi Gösterme
[FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md) bileşen yanı sıra bir yazı tipi seçin, boyut ve Ağırlık gibi görüntü özelliklerini değiştirmek kullanıcıların sağlar.  
  
 İletişim kutusunda seçili yazı tipi döndürülür <xref:System.Windows.Forms.FontDialog.Font%2A> özelliği. Bu nedenle, kullanıcı tarafından seçilen yazı tipi yararlanarak bir özelliği okuma olarak kadar kolaydır.  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a>FontDialog bileşeni kullanarak yazı tipi özellikleri seçmek için  
  
1.  İletişim kutusunu kullanarak görüntüleme <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.  
  
2.  Kullanım <xref:System.Windows.Forms.DialogResult> iletişim kutusunun nasıl kapatıldığını belirlemek için özellik.  
  
3.  Kullanım <xref:System.Windows.Forms.FontDialog.Font%2A> istenen yazı tipi ayarlamak için özellik.  
  
     Aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi açılır bir <xref:System.Windows.Forms.FontDialog> bileşeni. Bir yazı tipi seçilen ve kullanıcı olduğunda tıklar **Tamam**, <xref:System.Windows.Forms.FontDialog.Font%2A> özelliği bir <xref:System.Windows.Forms.TextBox> form üzerinde denetimi seçilen yazı tipi için ayarlanır. Formunuz sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetimi, bir <xref:System.Windows.Forms.TextBox> denetimi ve <xref:System.Windows.Forms.FontDialog> bileşeni.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FontDialog>  
 [FontDialog Bileşeni](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
