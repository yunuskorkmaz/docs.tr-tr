---
title: "Nasıl yapılır: Windows Forms RichTextBox Denetimi İçin Yazı Tipi Özniteliklerini Ayarlama"
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
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fe122f509890715c398bef728a98ff874b61817
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="4bdf2-102">Nasıl yapılır: Windows Forms RichTextBox Denetimi İçin Yazı Tipi Özniteliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="4bdf2-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="4bdf2-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi görüntülediği metni biçimlendirme için birçok seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="4bdf2-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="4bdf2-104">Seçilen karakterleri kalın, altı çizili ya da italik kullanarak yapabileceğiniz <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4bdf2-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="4bdf2-105">Bu özellik, boyutunu ve Seçilen karakterlerin yazı tipini değiştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bdf2-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="4bdf2-106"><xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Özelliği, seçilen karakterleri rengini değiştirmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="4bdf2-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="4bdf2-107">Karakterlerin görünümünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="4bdf2-107">To change the appearance of characters</span></span>  
  
1.  <span data-ttu-id="4bdf2-108">Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> uygun bir font özelliği.</span><span class="sxs-lookup"><span data-stu-id="4bdf2-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="4bdf2-109">Yazı tipi ailesi, boyutu ve yazı tipi bir uygulamada ayarlamak kullanıcıların etkinleştirmek için genellikle kullanacağınız <xref:System.Windows.Forms.FontDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="4bdf2-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="4bdf2-110">Genel bir bakış için bkz: [FontDialog bileşenine genel bakış](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4bdf2-110">For an overview, see [FontDialog Component Overview](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="4bdf2-111">Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> uygun bir renk özelliğine.</span><span class="sxs-lookup"><span data-stu-id="4bdf2-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="4bdf2-112">Bir uygulamada rengini ayarlamak kullanıcıların etkinleştirmek için genellikle kullanacağınız <xref:System.Windows.Forms.ColorDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="4bdf2-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="4bdf2-113">Genel bir bakış için bkz: [ColorDialog bileşenine genel bakış](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4bdf2-113">For an overview, see [ColorDialog Component Overview](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).</span></span>  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="4bdf2-114">Bu özellikler, yalnızca seçili metni etkiler veya metin seçtiyseniz olan metin ekleme noktasını geçerli konumda belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="4bdf2-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="4bdf2-115">Program aracılığıyla metni seçme hakkında daha fazla bilgi için bkz: <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="4bdf2-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdf2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4bdf2-116">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="4bdf2-117">RichTextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="4bdf2-117">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="4bdf2-118">Windows Forms'ta kullanılacak denetimler</span><span class="sxs-lookup"><span data-stu-id="4bdf2-118">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
