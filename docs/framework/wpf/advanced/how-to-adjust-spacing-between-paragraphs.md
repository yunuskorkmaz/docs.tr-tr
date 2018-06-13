---
title: 'Nasıl yapılır: Paragraflar Arasındaki Aralığı Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: b232903054cf45b70ba99a9223352391498cf79b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542954"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a><span data-ttu-id="eaac1-102">Nasıl yapılır: Paragraflar Arasındaki Aralığı Ayarlama</span><span class="sxs-lookup"><span data-stu-id="eaac1-102">How to: Adjust Spacing Between Paragraphs</span></span>
<span data-ttu-id="eaac1-103">Bu örnek, akış içeriğinde paragraflar arasındaki boşluğu ortadan kaldırmak veya ayarlamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eaac1-103">This example shows how to adjust or eliminate spacing between paragraphs in flow content.</span></span>  
  
 <span data-ttu-id="eaac1-104">Akış içeriği, paragraf arasında görünen boşluk üzerinde bu paragrafları ayarlama kenar boşluklarını sonucudur; Bu nedenle, bu paragrafları kenar boşluklarını ayarlayarak paragraflar arasındaki aralığı denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="eaac1-104">In flow content, extra space that appears between paragraphs is the result of margins set on these paragraphs; thus, the spacing between paragraphs can be controlled by adjusting the margins on those paragraphs.</span></span>  <span data-ttu-id="eaac1-105">İki paragraf arasında ek boşluk tamamen ortadan kaldırmak için paragraflara kenar boşluklarını ayarlama **0**.</span><span class="sxs-lookup"><span data-stu-id="eaac1-105">To eliminate extra spacing between two paragraphs altogether, set the margins for the paragraphs to **0**.</span></span>  <span data-ttu-id="eaac1-106">Tüm boyunca paragraflar arasında Tekdüzen aralığı elde etmek için <xref:System.Windows.Documents.FlowDocument>, tüm paragrafta Tekdüzen kenar boşluğu değerini ayarlamak için stil kullanın <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="eaac1-106">To achieve uniform spacing between paragraphs throughout an entire <xref:System.Windows.Documents.FlowDocument>, use styling to set a uniform margin value for all paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="eaac1-107">İki kenar boşluklarının büyük yerine ikiye yukarı iki bitişik Paragraf kenar boşluklarını "daraltıldığını" dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="eaac1-107">It is important to note that the margins for two adjacent paragraphs will "collapse" to the larger of the two margins, rather than doubling up.</span></span> <span data-ttu-id="eaac1-108">İki bitişik paragrafta 20 piksel ve 40 piksel kenar boşluklarını sırasıyla varsa, bu nedenle, sonuçta elde edilen paragraf arasında 40 piksel cinsinden iki kenar boşluğu değerinden daha büyük bir alandır.</span><span class="sxs-lookup"><span data-stu-id="eaac1-108">So, if two adjacent paragraphs have margins of 20 pixels and 40 pixels respectively, the resulting space between the paragraphs is 40 pixels, the larger of the two margin values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaac1-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="eaac1-109">Example</span></span>  
 <span data-ttu-id="eaac1-110">Aşağıdaki örnek, tüm kenar boşluğunu ayarlamak için stil kullanır <xref:System.Windows.Documents.Paragraph> öğelerinde bir <xref:System.Windows.Documents.FlowDocument> için **0**, etkili bir şekilde ortadan kaldırarak paragrafta arasında ek boşluk <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="eaac1-110">The following example uses styling to set the margin for all <xref:System.Windows.Documents.Paragraph> elements in a <xref:System.Windows.Documents.FlowDocument> to **0**, which effectively eliminates extra spacing between paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
