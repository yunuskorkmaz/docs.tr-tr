---
title: 'Nasıl yapılır: Metne Program Aracılığıyla Öğe Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Text Animation sample [WPF]
- elements [WPF], inserting into text
- inserting elements into text [WPF]
- TextPointer objects [WPF]
- text [WPF], inserting elements
ms.assetid: 97bd950a-25ac-4e42-a311-94b6420d4136
ms.openlocfilehash: c93a1c7542a4ddb33b3880de423c256adcc3f1c3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378567"
---
# <a name="how-to-insert-an-element-into-text-programmatically"></a><span data-ttu-id="4a809-102">Nasıl yapılır: Metne Program Aracılığıyla Öğe Ekleme</span><span class="sxs-lookup"><span data-stu-id="4a809-102">How to: Insert an Element Into Text Programmatically</span></span>
<span data-ttu-id="4a809-103">Aşağıdaki örnek nasıl kullanacağınızı gösterir <xref:System.Windows.Documents.TextPointer> metinde uygulamak için bir aralık belirtmek için nesneleri bir <xref:System.Windows.Documents.Span> öğesi.</span><span class="sxs-lookup"><span data-stu-id="4a809-103">The following example shows how to use two <xref:System.Windows.Documents.TextPointer> objects to specify a range within text to apply a <xref:System.Windows.Documents.Span> element to.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a809-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a809-104">Example</span></span>  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 <span data-ttu-id="4a809-105">Aşağıdaki çizimde, bu örnek nasıl göründüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a809-105">The illustration below shows what this example looks like.</span></span>  
  
 <span data-ttu-id="4a809-106">![Bir metin aralığı için uygulanan bir Span öğesi](./media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span><span class="sxs-lookup"><span data-stu-id="4a809-106">![A Span element applied to a range of text](./media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a809-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a809-107">See also</span></span>
- [<span data-ttu-id="4a809-108">Akış Belgesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4a809-108">Flow Document Overview</span></span>](flow-document-overview.md)
