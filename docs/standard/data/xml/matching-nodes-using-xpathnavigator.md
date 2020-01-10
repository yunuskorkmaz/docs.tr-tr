---
title: XPathNavigator Kullanarak Düğümleri Eşleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: f0988c3a112fefc351175de02c790dc25fe6e94a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710693"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="7894e-102">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="7894e-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="7894e-103"><xref:System.Xml.XPath.XPathNavigator> sınıfı, bir düğümün bir XPath ifadesiyle eşleşip eşleşmediğini anlamak için <xref:System.Xml.XPath.XPathNavigator.Matches%2A> yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7894e-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="7894e-104"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> yöntemi, giriş olarak bir XPath ifadesi alır ve geçerli düğümün verilen XPath ifadesiyle veya belirtilen derlenmiş <xref:System.Xml.XPath.XPathExpression> nesnesiyle eşleşip eşleşmediğini gösteren bir <xref:System.Boolean> döndürür.</span><span class="sxs-lookup"><span data-stu-id="7894e-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="7894e-105">Eşleşen düğümler</span><span class="sxs-lookup"><span data-stu-id="7894e-105">Matching Nodes</span></span>  
 <span data-ttu-id="7894e-106">Geçerli düğüm belirtilen XPath ifadesiyle eşleşiyorsa <xref:System.Xml.XPath.XPathNavigator.Matches%2A> yöntemi `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="7894e-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="7894e-107">Örneğin, aşağıdaki kod örneğinde, geçerli düğüm öğe `b`ise ve öğe `b` bir öznitelik `c`içeriyorsa <xref:System.Xml.XPath.XPathNavigator.Matches%2A> yöntemi `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="7894e-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7894e-108"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator>durumunu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="7894e-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7894e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7894e-109">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="7894e-110">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="7894e-110">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="7894e-111">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="7894e-111">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="7894e-112">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="7894e-112">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="7894e-113">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="7894e-113">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="7894e-114">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="7894e-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="7894e-115">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="7894e-115">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
