---
description: 'Daha fazla bilgi edinin: XPathNavigator kullanarak eşleşen düğümler'
title: XPathNavigator Kullanarak Düğümleri Eşleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: d142490829473d0891c5b2f18b1c3ec9e7ace426
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732013"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="3d079-103">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="3d079-103">Matching Nodes using XPathNavigator</span></span>

<span data-ttu-id="3d079-104"><xref:System.Xml.XPath.XPathNavigator>Sınıfı, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> bir düğümün bir XPath ifadesiyle eşleşip eşleşmediğini belirleme yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d079-104">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="3d079-105"><xref:System.Xml.XPath.XPathNavigator.Matches%2A>Yöntemi, giriş olarak bir XPath ifadesi alır ve <xref:System.Boolean> geçerli düğümün verilen XPath ifadesiyle veya belirtilen derlenmiş nesneyle eşleşip eşleşmediğini gösteren bir döndürür <xref:System.Xml.XPath.XPathExpression> .</span><span class="sxs-lookup"><span data-stu-id="3d079-105">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="3d079-106">Eşleşen düğümler</span><span class="sxs-lookup"><span data-stu-id="3d079-106">Matching Nodes</span></span>  

 <span data-ttu-id="3d079-107"><xref:System.Xml.XPath.XPathNavigator.Matches%2A>Yöntemi, `true` geçerli düğüm belirtilen XPath ifadesiyle eşleşiyorsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d079-107">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="3d079-108">Örneğin, aşağıdaki kod örneğinde, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> `true` geçerli düğüm öğesi ise `b` ve öğesinin bir özniteliği varsa yöntemi döndürülür `b` `c` .</span><span class="sxs-lookup"><span data-stu-id="3d079-108">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d079-109"><xref:System.Xml.XPath.XPathNavigator.Matches%2A>Yöntemi, öğesinin durumunu değiştirmez <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="3d079-109">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d079-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d079-110">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="3d079-111">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="3d079-111">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="3d079-112">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="3d079-112">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="3d079-113">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="3d079-113">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="3d079-114">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="3d079-114">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="3d079-115">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="3d079-115">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="3d079-116">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="3d079-116">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
