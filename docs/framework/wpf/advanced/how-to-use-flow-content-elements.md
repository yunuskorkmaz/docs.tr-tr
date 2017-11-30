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
ms.openlocfilehash: c1350a380e97631ac290e57de64fec696535fecc
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="8ece2-102">Nasıl yapılır: Akış İçeriği Öğelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="8ece2-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="8ece2-103">Aşağıdaki örnek, çeşitli içerik akışı öğeleri ve ilişkili öznitelikleri için bildirim kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ece2-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="8ece2-104">Gösterilen öğeler ve öznitelikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="8ece2-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="8ece2-105"><xref:System.Windows.Documents.Bold> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ece2-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="8ece2-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A>özniteliği</span><span class="sxs-lookup"><span data-stu-id="8ece2-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="8ece2-107"><xref:System.Windows.Documents.TextElement.FontSize%2A>özniteliği</span><span class="sxs-lookup"><span data-stu-id="8ece2-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="8ece2-108"><xref:System.Windows.Documents.Italic> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ece2-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="8ece2-109"><xref:System.Windows.Documents.LineBreak> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ece2-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="8ece2-110"><xref:System.Windows.Documents.List> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ece2-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="8ece2-111"><xref:System.Windows.Documents.ListItem> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ece2-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="8ece2-112"><xref:System.Windows.Documents.Paragraph> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ece2-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="8ece2-113"><xref:System.Windows.Documents.Run> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ece2-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="8ece2-114"><xref:System.Windows.Documents.Section> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ece2-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="8ece2-115"><xref:System.Windows.Documents.Span> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ece2-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="8ece2-116"><xref:System.Windows.Documents.Typography.Variants%2A>öznitelik (simgeyi ve alt simge)</span><span class="sxs-lookup"><span data-stu-id="8ece2-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="8ece2-117"><xref:System.Windows.Documents.Underline> öğesi</span><span class="sxs-lookup"><span data-stu-id="8ece2-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ece2-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ece2-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]
