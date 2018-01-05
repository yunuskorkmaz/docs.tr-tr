---
title: "Nasıl yapılır: Akış İçeriği Öğelerini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e637e114187d0864afe4211a45c346c1e5a449b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="e5a2e-102">Nasıl yapılır: Akış İçeriği Öğelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="e5a2e-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="e5a2e-103">Aşağıdaki örnek, çeşitli içerik akışı öğeleri ve ilişkili öznitelikleri için bildirim kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5a2e-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="e5a2e-104">Gösterilen öğeler ve öznitelikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="e5a2e-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="e5a2e-105"><xref:System.Windows.Documents.Bold> öğesi</span><span class="sxs-lookup"><span data-stu-id="e5a2e-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="e5a2e-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A>özniteliği</span><span class="sxs-lookup"><span data-stu-id="e5a2e-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="e5a2e-107"><xref:System.Windows.Documents.TextElement.FontSize%2A>özniteliği</span><span class="sxs-lookup"><span data-stu-id="e5a2e-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="e5a2e-108"><xref:System.Windows.Documents.Italic> öğesi</span><span class="sxs-lookup"><span data-stu-id="e5a2e-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="e5a2e-109"><xref:System.Windows.Documents.LineBreak> öğesi</span><span class="sxs-lookup"><span data-stu-id="e5a2e-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="e5a2e-110"><xref:System.Windows.Documents.List> öğesi</span><span class="sxs-lookup"><span data-stu-id="e5a2e-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="e5a2e-111"><xref:System.Windows.Documents.ListItem> öğesi</span><span class="sxs-lookup"><span data-stu-id="e5a2e-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="e5a2e-112"><xref:System.Windows.Documents.Paragraph> öğesi</span><span class="sxs-lookup"><span data-stu-id="e5a2e-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="e5a2e-113"><xref:System.Windows.Documents.Run> öğesi</span><span class="sxs-lookup"><span data-stu-id="e5a2e-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="e5a2e-114"><xref:System.Windows.Documents.Section> öğesi</span><span class="sxs-lookup"><span data-stu-id="e5a2e-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="e5a2e-115"><xref:System.Windows.Documents.Span> öğesi</span><span class="sxs-lookup"><span data-stu-id="e5a2e-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="e5a2e-116"><xref:System.Windows.Documents.Typography.Variants%2A>öznitelik (simgeyi ve alt simge)</span><span class="sxs-lookup"><span data-stu-id="e5a2e-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="e5a2e-117"><xref:System.Windows.Documents.Underline> öğesi</span><span class="sxs-lookup"><span data-stu-id="e5a2e-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5a2e-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5a2e-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]
