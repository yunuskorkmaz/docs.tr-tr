---
title: XPathNavigator kullanarak düğümleri eşleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 525c8332d2884415ccf883dae03866776510f354
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680432"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="b2e18-102">XPathNavigator kullanarak düğümleri eşleştirme</span><span class="sxs-lookup"><span data-stu-id="b2e18-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="b2e18-103"><xref:System.Xml.XPath.XPathNavigator> Sağlar sınıfını <xref:System.Xml.XPath.XPathNavigator.Matches%2A> bir düğüm bir XPath ifadesi eşleşip eşleşmediğini belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b2e18-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="b2e18-104"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi bir XPath ifadesini girdi olarak alır ve döndürür bir <xref:System.Boolean> geçerli düğüm, belirli bir XPath ifadesi eşleşip eşleşmediğini gösterir veya derlenmiş verilen <xref:System.Xml.XPath.XPathExpression> nesne.</span><span class="sxs-lookup"><span data-stu-id="b2e18-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="b2e18-105">Eşleşen düğümleri</span><span class="sxs-lookup"><span data-stu-id="b2e18-105">Matching Nodes</span></span>  
 <span data-ttu-id="b2e18-106"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi döndürür `true` belirtilen XPath ifadesi geçerli düğüm eşleşmesi durumunda.</span><span class="sxs-lookup"><span data-stu-id="b2e18-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="b2e18-107">Örneğin, aşağıdaki kod örneğinde <xref:System.Xml.XPath.XPathNavigator.Matches%2A> yöntemi döndürür `true` geçerli düğüm öğesi ise `b`ve öğe `b` öznitelikle `c`.</span><span class="sxs-lookup"><span data-stu-id="b2e18-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2e18-108"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi durumunu değiştirmez <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="b2e18-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2e18-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2e18-109">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="b2e18-110">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="b2e18-110">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="b2e18-111">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="b2e18-111">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="b2e18-112">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="b2e18-112">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="b2e18-113">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="b2e18-113">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="b2e18-114">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="b2e18-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="b2e18-115">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="b2e18-115">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
