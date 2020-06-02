---
title: XPathNavigator Kullanarak Düğümleri Eşleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: 47b0ba7e705ad602825dcca3f24c207362174a4c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289128"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="1e59a-102">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="1e59a-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="1e59a-103"><xref:System.Xml.XPath.XPathNavigator>Sınıfı, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> bir düğümün bir XPath ifadesiyle eşleşip eşleşmediğini belirleme yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e59a-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="1e59a-104"><xref:System.Xml.XPath.XPathNavigator.Matches%2A>Yöntemi, giriş olarak bir XPath ifadesi alır ve <xref:System.Boolean> geçerli düğümün verilen XPath ifadesiyle veya belirtilen derlenmiş nesneyle eşleşip eşleşmediğini gösteren bir döndürür <xref:System.Xml.XPath.XPathExpression> .</span><span class="sxs-lookup"><span data-stu-id="1e59a-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="1e59a-105">Eşleşen düğümler</span><span class="sxs-lookup"><span data-stu-id="1e59a-105">Matching Nodes</span></span>  
 <span data-ttu-id="1e59a-106"><xref:System.Xml.XPath.XPathNavigator.Matches%2A>Yöntemi, `true` geçerli düğüm belirtilen XPath ifadesiyle eşleşiyorsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e59a-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="1e59a-107">Örneğin, aşağıdaki kod örneğinde, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> `true` geçerli düğüm öğesi ise `b` ve öğesinin bir özniteliği varsa yöntemi döndürülür `b` `c` .</span><span class="sxs-lookup"><span data-stu-id="1e59a-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e59a-108"><xref:System.Xml.XPath.XPathNavigator.Matches%2A>Yöntemi, öğesinin durumunu değiştirmez <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="1e59a-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e59a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e59a-109">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="1e59a-110">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="1e59a-110">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="1e59a-111">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="1e59a-111">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="1e59a-112">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="1e59a-112">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="1e59a-113">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="1e59a-113">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="1e59a-114">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="1e59a-114">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="1e59a-115">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="1e59a-115">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
