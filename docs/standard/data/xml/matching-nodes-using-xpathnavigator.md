---
title: XPathNavigator Kullanarak Düğümleri Eşleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882e92c6c8cb6e638ca299ed4c43b9da8f4bf235
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923320"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="3cbe0-102">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="3cbe0-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="3cbe0-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı ,<xref:System.Xml.XPath.XPathNavigator.Matches%2A> bir düğümün bir XPath ifadesiyle eşleşip eşleşmediğini belirleme yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cbe0-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="3cbe0-104">Yöntemi <xref:System.Xml.XPath.XPathNavigator.Matches%2A> , giriş olarak bir XPath ifadesi alır ve geçerli düğümün <xref:System.Boolean> verilen XPath ifadesiyle veya belirtilen derlenmiş <xref:System.Xml.XPath.XPathExpression> nesneyle eşleşip eşleşmediğini gösteren bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="3cbe0-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="3cbe0-105">Eşleşen düğümler</span><span class="sxs-lookup"><span data-stu-id="3cbe0-105">Matching Nodes</span></span>  
 <span data-ttu-id="3cbe0-106">Yöntemi, geçerli düğüm belirtilen XPath ifadesiyle eşleşiyorsa döndürür `true`. <xref:System.Xml.XPath.XPathNavigator.Matches%2A></span><span class="sxs-lookup"><span data-stu-id="3cbe0-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="3cbe0-107">Örneğin, aşağıdaki kod örneğinde, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> geçerli düğüm öğesi `b`ise ve öğesinin `b` bir özniteliği `true` `c`varsa yöntemi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="3cbe0-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cbe0-108"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi ,<xref:System.Xml.XPath.XPathNavigator>öğesinin durumunu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="3cbe0-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3cbe0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cbe0-109">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="3cbe0-110">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="3cbe0-110">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="3cbe0-111">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="3cbe0-111">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="3cbe0-112">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="3cbe0-112">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="3cbe0-113">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="3cbe0-113">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="3cbe0-114">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="3cbe0-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="3cbe0-115">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="3cbe0-115">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
