---
title: 'Nasıl yapılır: Paragraflar Arasındaki Aralığı Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: e2a6ba34e3ab15eb316671fef7c11bea03d53c73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777019"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a><span data-ttu-id="6f54f-102">Nasıl yapılır: Paragraflar Arasındaki Aralığı Ayarlama</span><span class="sxs-lookup"><span data-stu-id="6f54f-102">How to: Adjust Spacing Between Paragraphs</span></span>
<span data-ttu-id="6f54f-103">Bu örnekte, akış içerik paragraflar arasındaki aralığı ortadan kaldırmak veya ayarlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f54f-103">This example shows how to adjust or eliminate spacing between paragraphs in flow content.</span></span>  
  
 <span data-ttu-id="6f54f-104">Akış içeriği, görünen paragraflar arasındaki boşluk kenar boşlukları paragraflarda ayarlayın sonucudur; Bu nedenle, bu paragraflardaki kenar boşluklarını ayarlayarak paragraflar arasındaki aralığı denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="6f54f-104">In flow content, extra space that appears between paragraphs is the result of margins set on these paragraphs; thus, the spacing between paragraphs can be controlled by adjusting the margins on those paragraphs.</span></span>  <span data-ttu-id="6f54f-105">İki paragraflar arasındaki fazladan aralığı tamamen ortadan kaldırmak için paragraflara kenar boşluklarını ayarlama **0**.</span><span class="sxs-lookup"><span data-stu-id="6f54f-105">To eliminate extra spacing between two paragraphs altogether, set the margins for the paragraphs to **0**.</span></span>  <span data-ttu-id="6f54f-106">Tüm boyunca paragraflar arasındaki Tekdüzen aralığı elde etmek için <xref:System.Windows.Documents.FlowDocument>, tüm bir Tekdüzen kenar boşluğu değerini ayarlamak için stil kullanın <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="6f54f-106">To achieve uniform spacing between paragraphs throughout an entire <xref:System.Windows.Documents.FlowDocument>, use styling to set a uniform margin value for all paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="6f54f-107">İki bitişik Paragraf kenar boşluklarını "daraltıldığını" iki kenar boşluklarının büyük yerine ikiye yukarı dikkat edin önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6f54f-107">It is important to note that the margins for two adjacent paragraphs will "collapse" to the larger of the two margins, rather than doubling up.</span></span> <span data-ttu-id="6f54f-108">İki bitişik paragraflar ve 20 40 pikseller kenar boşluklarını sırasıyla varsa, bu nedenle, sonuçta elde edilen alan paragraflar arasındaki 40, iki kenar boşluğu değerleri büyük pikseldir.</span><span class="sxs-lookup"><span data-stu-id="6f54f-108">So, if two adjacent paragraphs have margins of 20 pixels and 40 pixels respectively, the resulting space between the paragraphs is 40 pixels, the larger of the two margin values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f54f-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f54f-109">Example</span></span>  
 <span data-ttu-id="6f54f-110">Aşağıdaki örnek, tüm kenar boşluklarını ayarlamak için stil kullanır. <xref:System.Windows.Documents.Paragraph> öğelerinde bir <xref:System.Windows.Documents.FlowDocument> için **0**, etkili bir şekilde ortadan kaldırarak paragraflarda arasında ek boşluk <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="6f54f-110">The following example uses styling to set the margin for all <xref:System.Windows.Documents.Paragraph> elements in a <xref:System.Windows.Documents.FlowDocument> to **0**, which effectively eliminates extra spacing between paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
