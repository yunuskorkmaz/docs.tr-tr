---
title: 'Nasıl yapılır: FlowDocument Sütun Ayırıcı Öznitelikleri Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 27491b21da587fa198061ba52d8daed5d3f28de3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032051"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a><span data-ttu-id="55650-102">Nasıl yapılır: FlowDocument Sütun Ayırıcı Öznitelikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="55650-102">How to: Use FlowDocument Column-Separating Attributes</span></span>
<span data-ttu-id="55650-103">Bu örnek, sütun ayırıcı özelliklerini kullanmayı gösterir. bir <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="55650-103">This example shows how to use the column-separating features of a <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55650-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="55650-104">Example</span></span>  
 <span data-ttu-id="55650-105">Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.Documents.FlowDocument>ve ayarlar <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, ve <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="55650-105">The following example defines a <xref:System.Windows.Documents.FlowDocument>, and sets the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes.</span></span>  <span data-ttu-id="55650-106"><xref:System.Windows.Documents.FlowDocument> Örnek içerik tek bir paragraf içerir.</span><span class="sxs-lookup"><span data-stu-id="55650-106">The <xref:System.Windows.Documents.FlowDocument> contains a single paragraph of sample content.</span></span>  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 <span data-ttu-id="55650-107">Aşağıdaki şekil etkilerini gösterir <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, ve <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> işlenen özniteliklerinde <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="55650-107">The following figure shows the effects of the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes in a rendered <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 ![FlowDocument Sütun içi öznitelik gösteren ekran görüntüsü.](./media/how-to-use-flowdocument-column-separating-attributes/flowdocument-intra-column.png)
