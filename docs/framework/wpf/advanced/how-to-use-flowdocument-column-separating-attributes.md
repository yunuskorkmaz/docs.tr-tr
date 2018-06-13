---
title: 'Nasıl yapılır: FlowDocument Sütun Ayırıcı Öznitelikleri Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 678e01a35c286ea03f0385291d64f2f900f068c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543777"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a><span data-ttu-id="a578e-102">Nasıl yapılır: FlowDocument Sütun Ayırıcı Öznitelikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="a578e-102">How to: Use FlowDocument Column-Separating Attributes</span></span>
<span data-ttu-id="a578e-103">Bu örnek, sütun ayırıcı özelliklerinin nasıl kullanılacağını gösterir bir <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="a578e-103">This example shows how to use the column-separating features of a <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a578e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a578e-104">Example</span></span>  
 <span data-ttu-id="a578e-105">Aşağıdaki örnek tanımlayan bir <xref:System.Windows.Documents.FlowDocument>ve ayarlar <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, ve <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="a578e-105">The following example defines a <xref:System.Windows.Documents.FlowDocument>, and sets the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes.</span></span>  <span data-ttu-id="a578e-106"><xref:System.Windows.Documents.FlowDocument> Örnek içeriğin tek bir paragraf içerir.</span><span class="sxs-lookup"><span data-stu-id="a578e-106">The <xref:System.Windows.Documents.FlowDocument> contains a single paragraph of sample content.</span></span>  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 <span data-ttu-id="a578e-107">Aşağıdaki şekilde gösterilmiştir etkilerini <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, ve <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> öznitelikleri işlenmiş <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="a578e-107">The following figure shows the effects of the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes in a rendered <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="a578e-108">![Ekran görüntüsü: FlowDocument Sütun içi](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")</span><span class="sxs-lookup"><span data-stu-id="a578e-108">![Screenshot: FlowDocument Intra Column](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")</span></span>
