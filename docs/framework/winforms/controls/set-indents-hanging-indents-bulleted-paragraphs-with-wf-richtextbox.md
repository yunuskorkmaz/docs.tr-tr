---
title: RichTextBox denetimi ile girintileri, asılı girintileri ve madde Işaretli paragrafları ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
ms.openlocfilehash: 4dcd5691f328eac6d94675c50ed41a7d7cc36596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743008"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="56e3f-102">Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Girintileri, Asılı Girintileri ve Madde İşaretli Paragrafları Ayarlama</span><span class="sxs-lookup"><span data-stu-id="56e3f-102">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="56e3f-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, görüntülediği metni biçimlendirmek için çeşitli seçeneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="56e3f-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="56e3f-104"><xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliğini ayarlayarak seçili paragrafları madde işaretli listeler olarak biçimlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56e3f-104">You can format selected paragraphs as bulleted lists by setting the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="56e3f-105"><xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>ve <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> özelliklerini, denetimin sol ve sağ kenarlarına ve diğer metin satırlarının sol kenarına göre ayarlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56e3f-105">You can also use the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, and <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> properties to set the indentation of paragraphs relative to the left and right edges of the control, and the left edge of other lines of text.</span></span>  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a><span data-ttu-id="56e3f-106">Paragrafı madde işaretli liste olarak biçimlendirmek için</span><span class="sxs-lookup"><span data-stu-id="56e3f-106">To format a paragraph as a bulleted list</span></span>  
  
1. <span data-ttu-id="56e3f-107">Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="56e3f-107">Set the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property to `true`.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a><span data-ttu-id="56e3f-108">Paragrafı girintilemek için</span><span class="sxs-lookup"><span data-stu-id="56e3f-108">To indent a paragraph</span></span>  
  
1. <span data-ttu-id="56e3f-109"><xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> özelliğini, denetimin sol kenarı ve metnin sol kenarı arasında piksel cinsinden uzaklığı temsil eden bir tamsayı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="56e3f-109">Set the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> property to an integer representing the distance in pixels between the left edge of the control and the left edge of the text.</span></span>  
  
2. <span data-ttu-id="56e3f-110"><xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> özelliğini, paragraftaki metnin sol kenarı ve aynı paragraftaki sonraki satırların sol kenarı arasındaki mesafeyi temsil eden bir tamsayı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="56e3f-110">Set the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property to an integer representing the distance in pixels between the left edge of the first line of text in the paragraph and the left edge of subsequent lines in the same paragraph.</span></span> <span data-ttu-id="56e3f-111"><xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> özelliğinin değeri yalnızca, ilk satırın altına kaydırılmış olan bir paragraftaki satırlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="56e3f-111">The value of the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property only applies to lines in a paragraph that have wrapped below the first line.</span></span>  
  
3. <span data-ttu-id="56e3f-112"><xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> özelliğini, denetimin sağ kenarı ve metnin sağ kenarı arasındaki mesafeyi temsil eden bir tamsayı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="56e3f-112">Set the <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> property to an integer representing the distance in pixels between the right edge of the control and the right edge of the text.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="56e3f-113">Tüm bu özellikler, seçili metni içeren paragrafları ve ayrıca geçerli ekleme noktasının ardından yazılan metni etkiler.</span><span class="sxs-lookup"><span data-stu-id="56e3f-113">All these properties affect any paragraphs that contain selected text, and also the text that is typed after the current insertion point.</span></span> <span data-ttu-id="56e3f-114">Örneğin, bir Kullanıcı bir paragraf içinde bir kelime seçip Girintiyi ayarladığında, yeni ayarlar, bu sözcüğü içeren tüm paragrafa ve ayrıca seçili paragraftan sonra daha sonra girilmiş olan paragraflara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="56e3f-114">For example, when a user selects a word within a paragraph and then adjusts the indentation, the new settings will apply to the entire paragraph that contains that word, and also to any paragraphs subsequently entered after the selected paragraph.</span></span> <span data-ttu-id="56e3f-115">Program aracılığıyla metin seçme hakkında daha fazla bilgi için bkz. <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="56e3f-115">For information about selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e3f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56e3f-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="56e3f-117">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="56e3f-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="56e3f-118">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="56e3f-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
