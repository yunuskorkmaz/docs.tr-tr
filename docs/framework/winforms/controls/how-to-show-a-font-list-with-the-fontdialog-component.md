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
ms.openlocfilehash: 781daeb43a952ef25e73edd577fa17c61b02b426
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a><span data-ttu-id="97bd7-102">Nasıl Yapılır: FontDialog Bileşeni ile Yazı Tipi Listesi Gösterme</span><span class="sxs-lookup"><span data-stu-id="97bd7-102">How to: Show a Font List with the FontDialog Component</span></span>
<span data-ttu-id="97bd7-103">[FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md) bileşen yanı sıra bir yazı tipi seçin, boyut ve Ağırlık gibi görüntü özelliklerini değiştirmek kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="97bd7-103">The [FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md) component allows users to select a font, as well as change its display aspects, such as its weight and size.</span></span>  
  
 <span data-ttu-id="97bd7-104">İletişim kutusunda seçili yazı tipi döndürülür <xref:System.Windows.Forms.FontDialog.Font%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="97bd7-104">The font selected in the dialog box is returned in the <xref:System.Windows.Forms.FontDialog.Font%2A> property.</span></span> <span data-ttu-id="97bd7-105">Bu nedenle, kullanıcı tarafından seçilen yazı tipi yararlanarak bir özelliği okuma olarak kadar kolaydır.</span><span class="sxs-lookup"><span data-stu-id="97bd7-105">Thus, taking advantage of the font selected by the user is as easy as reading a property.</span></span>  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a><span data-ttu-id="97bd7-106">FontDialog bileşeni kullanarak yazı tipi özellikleri seçmek için</span><span class="sxs-lookup"><span data-stu-id="97bd7-106">To select font properties using the FontDialog Component</span></span>  
  
1.  <span data-ttu-id="97bd7-107">İletişim kutusunu kullanarak görüntüleme <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="97bd7-107">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2.  <span data-ttu-id="97bd7-108">Kullanım <xref:System.Windows.Forms.DialogResult> iletişim kutusunun nasıl kapatıldığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="97bd7-108">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3.  <span data-ttu-id="97bd7-109">Kullanım <xref:System.Windows.Forms.FontDialog.Font%2A> istenen yazı tipi ayarlamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="97bd7-109">Use the <xref:System.Windows.Forms.FontDialog.Font%2A> property to set the desired font.</span></span>  
  
     <span data-ttu-id="97bd7-110">Aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi açılır bir <xref:System.Windows.Forms.FontDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="97bd7-110">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="97bd7-111">Bir yazı tipi seçilen ve kullanıcı olduğunda tıklar **Tamam**, <xref:System.Windows.Forms.FontDialog.Font%2A> özelliği bir <xref:System.Windows.Forms.TextBox> form üzerinde denetimi seçilen yazı tipi için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="97bd7-111">When a font is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.FontDialog.Font%2A> property of a <xref:System.Windows.Forms.TextBox> control that is on the form is set to the chosen font.</span></span> <span data-ttu-id="97bd7-112">Formunuz sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetimi, bir <xref:System.Windows.Forms.TextBox> denetimi ve <xref:System.Windows.Forms.FontDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="97bd7-112">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a  <xref:System.Windows.Forms.TextBox> control, and a <xref:System.Windows.Forms.FontDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="97bd7-113">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="97bd7-113">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="97bd7-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97bd7-114">See Also</span></span>  
 <xref:System.Windows.Forms.FontDialog>  
 [<span data-ttu-id="97bd7-115">FontDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="97bd7-115">FontDialog Component</span></span>](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
