---
title: "Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Girintileri, Asılı Girintileri ve Madde İşaretli Paragrafları Ayarlama"
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
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1349e86ecd04c0d4e394e7939996c3e717e841e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="07bd3-102">Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Girintileri, Asılı Girintileri ve Madde İşaretli Paragrafları Ayarlama</span><span class="sxs-lookup"><span data-stu-id="07bd3-102">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="07bd3-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi görüntülediği metni biçimlendirme için birçok seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="07bd3-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="07bd3-104">Ayarlayarak seçili paragrafları madde işaretli listeler olarak biçimlendirebilirsiniz <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="07bd3-104">You can format selected paragraphs as bulleted lists by setting the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="07bd3-105">Aynı zamanda <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, ve <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> paragrafları sol ve sağ kenarlarının denetimi ve diğer satırlar metnin sol kenarı göre girinti ayarlamak için özellikleri.</span><span class="sxs-lookup"><span data-stu-id="07bd3-105">You can also use the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, and <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> properties to set the indentation of paragraphs relative to the left and right edges of the control, and the left edge of other lines of text.</span></span>  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a><span data-ttu-id="07bd3-106">Madde işaretli bir liste olarak bir paragraf biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="07bd3-106">To format a paragraph as a bulleted list</span></span>  
  
1.  <span data-ttu-id="07bd3-107">Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="07bd3-107">Set the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property to `true`.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a><span data-ttu-id="07bd3-108">Paragrafın girinti</span><span class="sxs-lookup"><span data-stu-id="07bd3-108">To indent a paragraph</span></span>  
  
1.  <span data-ttu-id="07bd3-109">Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> denetimi sol kenarı ve metnin sol köşesinde arasındaki piksel cinsinden uzaklık temsil eden bir tamsayı özelliği.</span><span class="sxs-lookup"><span data-stu-id="07bd3-109">Set the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> property to an integer representing the distance in pixels between the left edge of the control and the left edge of the text.</span></span>  
  
2.  <span data-ttu-id="07bd3-110">Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> paragraf içindeki metnin ilk satırın sol kenarı ve sonraki satırların aynı paragrafta sol kenarı arasındaki piksel cinsinden uzaklığı temsil eden bir tamsayı özelliği.</span><span class="sxs-lookup"><span data-stu-id="07bd3-110">Set the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property to an integer representing the distance in pixels between the left edge of the first line of text in the paragraph and the left edge of subsequent lines in the same paragraph.</span></span> <span data-ttu-id="07bd3-111">Değeri <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> özelliği yalnızca uygulanır altına ilk satır Sarmalanan bir paragraf satırlarında.</span><span class="sxs-lookup"><span data-stu-id="07bd3-111">The value of the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property only applies to lines in a paragraph that have wrapped below the first line.</span></span>  
  
3.  <span data-ttu-id="07bd3-112">Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> denetimin sağ kenarı ve metnin sağ köşesine arasındaki piksel cinsinden uzaklığı temsil eden bir tamsayı özelliği.</span><span class="sxs-lookup"><span data-stu-id="07bd3-112">Set the <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> property to an integer representing the distance in pixels between the right edge of the control and the right edge of the text.</span></span>  
  
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
    >  <span data-ttu-id="07bd3-113">Bu özellikleri seçili metin ve sonra geçerli ekleme noktasını yazılan metni içeren tüm paragrafları etkiler.</span><span class="sxs-lookup"><span data-stu-id="07bd3-113">All these properties affect any paragraphs that contain selected text, and also the text that is typed after the current insertion point.</span></span> <span data-ttu-id="07bd3-114">Örneğin, bir kullanıcı bir paragraf içinde bir sözcük seçer ve girinti ayarlar, yeni ayarları bu sözcüğünü içeren tüm paragrafı ve ayrıca daha sonra seçili paragrafın girilen paragrafları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="07bd3-114">For example, when a user selects a word within a paragraph and then adjusts the indentation, the new settings will apply to the entire paragraph that contains that word, and also to any paragraphs subsequently entered after the selected paragraph.</span></span> <span data-ttu-id="07bd3-115">Program aracılığıyla metni seçme hakkında daha fazla bilgi için bkz: <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="07bd3-115">For information about selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07bd3-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07bd3-116">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="07bd3-117">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="07bd3-117">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="07bd3-118">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="07bd3-118">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
