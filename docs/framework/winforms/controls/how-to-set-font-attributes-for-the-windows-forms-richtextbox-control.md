---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetimi İçin Yazı Tipi Özniteliklerini Ayarlama'
ms.date: 03/30/2017
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
ms.openlocfilehash: 4919e94c23b1a67680ea0f360304ee0f75c7f425
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963218"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="95c0c-102">Nasıl yapılır: Windows Forms RichTextBox Denetimi İçin Yazı Tipi Özniteliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="95c0c-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="95c0c-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, görüntülediği metni biçimlendirmek için çeşitli seçeneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="95c0c-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="95c0c-104"><xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> Özelliği kullanarak seçili karakterleri kalın, altı çizili veya italik yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95c0c-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="95c0c-105">Bu özelliği, seçilen karakterlerin boyutunu ve yazı tipini değiştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95c0c-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="95c0c-106">Özelliği <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> , seçilen karakterlerin rengini değiştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="95c0c-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="95c0c-107">Karakterlerin görünüşünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="95c0c-107">To change the appearance of characters</span></span>  
  
1. <span data-ttu-id="95c0c-108"><xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> Özelliği uygun bir yazı tipine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="95c0c-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="95c0c-109">Kullanıcıların bir uygulamadaki yazı tipi ailesini, boyutunu ve yazı tipini ayarlayacağından, genellikle <xref:System.Windows.Forms.FontDialog> bileşeni kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="95c0c-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="95c0c-110">Genel bakış için bkz. [FontDialog bileşenine genel bakış](fontdialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="95c0c-110">For an overview, see [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="95c0c-111"><xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Özelliği uygun bir renge ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="95c0c-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="95c0c-112">Kullanıcıların bir uygulamada renk ayarlaması için, genellikle <xref:System.Windows.Forms.ColorDialog> bileşenini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="95c0c-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="95c0c-113">Genel bakış için bkz. [ColorDialog Bileşenine Genel Bakış](colordialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="95c0c-113">For an overview, see [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).</span></span>  
  
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
    > <span data-ttu-id="95c0c-114">Bu özellikler yalnızca seçili metni etkiler veya hiçbir metin seçilmezse, ekleme noktasının geçerli konumuna yazılan metni.</span><span class="sxs-lookup"><span data-stu-id="95c0c-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="95c0c-115">Program aracılığıyla metin seçme hakkında bilgi için bkz <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="95c0c-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c0c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95c0c-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="95c0c-117">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="95c0c-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="95c0c-118">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="95c0c-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
