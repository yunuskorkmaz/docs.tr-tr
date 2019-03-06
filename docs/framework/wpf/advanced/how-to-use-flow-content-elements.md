---
title: 'Nasıl yapılır: Akış İçeriği Öğelerini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
ms.openlocfilehash: df591304736adf1725b2b4235149bd426fe15216
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368118"
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="8ac22-102">Nasıl yapılır: Akış İçeriği Öğelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="8ac22-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="8ac22-103">Aşağıdaki örnek, çeşitli akış içeriği öğelerini ve ilişkili öznitelikleri için bildirim kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ac22-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="8ac22-104">Gösterilen öğeler ve öznitelikler içerir:</span><span class="sxs-lookup"><span data-stu-id="8ac22-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="8ac22-105"><xref:System.Windows.Documents.Bold> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ac22-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="8ac22-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> Özniteliği</span><span class="sxs-lookup"><span data-stu-id="8ac22-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="8ac22-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> Özniteliği</span><span class="sxs-lookup"><span data-stu-id="8ac22-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="8ac22-108"><xref:System.Windows.Documents.Italic> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ac22-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="8ac22-109"><xref:System.Windows.Documents.LineBreak> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ac22-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="8ac22-110"><xref:System.Windows.Documents.List> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ac22-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="8ac22-111"><xref:System.Windows.Documents.ListItem> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ac22-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="8ac22-112"><xref:System.Windows.Documents.Paragraph> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ac22-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="8ac22-113"><xref:System.Windows.Documents.Run> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ac22-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="8ac22-114"><xref:System.Windows.Documents.Section> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ac22-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="8ac22-115"><xref:System.Windows.Documents.Span> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ac22-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="8ac22-116"><xref:System.Windows.Documents.Typography.Variants%2A> öznitelik (üst simge ve alt simge)</span><span class="sxs-lookup"><span data-stu-id="8ac22-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="8ac22-117"><xref:System.Windows.Documents.Underline> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ac22-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ac22-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ac22-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]
