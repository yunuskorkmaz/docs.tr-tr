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
ms.openlocfilehash: 10aff89679d5c8099d5128540521879f10e3e294
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041203"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="afaa3-102">XPathNavigator kullanarak düğümleri eşleştirme</span><span class="sxs-lookup"><span data-stu-id="afaa3-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="afaa3-103"><xref:System.Xml.XPath.XPathNavigator> Sağlar sınıfını <xref:System.Xml.XPath.XPathNavigator.Matches%2A> bir düğüm bir XPath ifadesi eşleşip eşleşmediğini belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="afaa3-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="afaa3-104"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi bir XPath ifadesini girdi olarak alır ve döndürür bir <xref:System.Boolean> geçerli düğüm, belirli bir XPath ifadesi eşleşip eşleşmediğini gösterir veya derlenmiş verilen <xref:System.Xml.XPath.XPathExpression> nesne.</span><span class="sxs-lookup"><span data-stu-id="afaa3-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="afaa3-105">Eşleşen düğümleri</span><span class="sxs-lookup"><span data-stu-id="afaa3-105">Matching Nodes</span></span>  
 <span data-ttu-id="afaa3-106"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi döndürür `true` belirtilen XPath ifadesi geçerli düğüm eşleşmesi durumunda.</span><span class="sxs-lookup"><span data-stu-id="afaa3-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="afaa3-107">Örneğin, aşağıdaki kod örneğinde <xref:System.Xml.XPath.XPathNavigator.Matches%2A> yöntemi döndürür `true` geçerli düğüm öğesi ise `b`ve öğe `b` öznitelikle `c`.</span><span class="sxs-lookup"><span data-stu-id="afaa3-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afaa3-108"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi durumunu değiştirmez <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="afaa3-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="afaa3-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afaa3-109">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="afaa3-110">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="afaa3-110">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="afaa3-111">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="afaa3-111">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="afaa3-112">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="afaa3-112">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
- [<span data-ttu-id="afaa3-113">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="afaa3-113">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [<span data-ttu-id="afaa3-114">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="afaa3-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
- [<span data-ttu-id="afaa3-115">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="afaa3-115">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
