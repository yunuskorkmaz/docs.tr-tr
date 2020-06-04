---
title: 'Nasıl yapılır: Belirli Bir Alt Öğeye Sahip Öğeyi Bulma'
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: a05504070fe3d2ea5eb6135fd3bf697b131686c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405293"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a><span data-ttu-id="cd4bb-102">Nasıl yapılır: belirli bir alt öğeye sahip bir öğe bulma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd4bb-102">How to: Find an Element with a Specific Child Element (Visual Basic)</span></span>
<span data-ttu-id="cd4bb-103">Bu konu, belirli bir değere sahip bir alt öğesi olan belirli bir öğenin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd4bb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd4bb-104">Example</span></span>  
 <span data-ttu-id="cd4bb-105">Örnek, `Test` `CommandLine` "EXAMP2. exe" değerine sahip bir alt öğesi olan öğesini bulur.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="cd4bb-106">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: test yapılandırması (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cd4bb-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("TestConfig.xml")  
Dim tests As IEnumerable(Of XElement) = _  
    From el In root.<Test> _  
    Where el.<CommandLine>.Value = "Examp2.EXE" _  
    Select el  
For Each el as XElement In tests  
    Console.WriteLine(el.@TestId)  
Next  
```  
  
 <span data-ttu-id="cd4bb-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cd4bb-107">This code produces the following output:</span></span>  
  
```console  
0002  
0006  
```  
  
 <span data-ttu-id="cd4bb-108">Bu örnekte XML [alt eksen özelliği](../../../language-reference/xml-axis/xml-child-axis-property.md), [XML özniteliği eksen özelliği](../../../language-reference/xml-axis/xml-attribute-axis-property.md)ve [XML değeri özelliği](../../../language-reference/xml-axis/xml-value-property.md)kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-108">Note that this example uses the [XML Child axis property](../../../language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../../language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../../language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd4bb-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd4bb-109">Example</span></span>  
 <span data-ttu-id="cd4bb-110">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="cd4bb-111">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cd4bb-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="cd4bb-112">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında test yapılandırması](sample-xml-file-test-configuration-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="cd4bb-112">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](sample-xml-file-test-configuration-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")  
        Dim tests As IEnumerable(Of XElement) = _  
            From el In root.<Test> _  
            Where el.<CommandLine>.Value = "Examp2.EXE" _  
            Select el  
        For Each el As XElement In tests  
            Console.WriteLine(el.@TestId)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="cd4bb-113">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cd4bb-113">This code produces the following output:</span></span>  
  
```console  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd4bb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd4bb-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="cd4bb-115">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd4bb-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
- [<span data-ttu-id="cd4bb-116">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd4bb-116">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="cd4bb-117">Projeksiyon Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd4bb-117">Projection Operations (Visual Basic)</span></span>](projection-operations.md)
