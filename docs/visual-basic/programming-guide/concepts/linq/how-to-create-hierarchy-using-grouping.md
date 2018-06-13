---
title: 'Nasıl yapılır: gruplandırma (Visual Basic) kullanarak hiyerarşi oluşturma'
ms.date: 07/20/2015
ms.assetid: 4eb3ca6b-1aed-43de-b8b9-41c769c993f8
ms.openlocfilehash: 9df85a52d63c4d7dbffb99a47378d3a1efc10cca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639330"
---
# <a name="how-to-create-hierarchy-using-grouping-visual-basic"></a><span data-ttu-id="ae406-102">Nasıl yapılır: gruplandırma (Visual Basic) kullanarak hiyerarşi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ae406-102">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>
<span data-ttu-id="ae406-103">Bu örnek, verileri gruplandırmak ve XML gruplandırılması tabanlı oluşturmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ae406-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae406-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae406-104">Example</span></span>  
 <span data-ttu-id="ae406-105">Bu örnek ilk grupları verileri bir kategoriye göre sonra XML hiyerarşisini gruplandırma yansıtır yeni bir XML dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ae406-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="ae406-106">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: sayısal verileri (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ae406-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim doc As XElement = XElement.Load("Data.xml")  
Dim newData As XElement = _  
    <Root>  
        <%= _  
            From data In doc.<Data> _  
            Group By category = data.<Category>(0).Value _  
            Into groupedData = Group _  
            Select <Group ID=<%= category %>>  
                       <%= _  
                           From g In groupedData _  
                           Select _  
                           <Data>  
                               <%= g.<Quantity>(0) %>  
                               <%= g.<Price>(0) %>  
                           </Data> _  
                       %>  
                   </Group> _  
        %>  
    </Root>  
Console.WriteLine(newData)  
```  
  
 <span data-ttu-id="ae406-107">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="ae406-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Group ID="A">  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>24.50</Price>  
    </Data>  
    <Data>  
      <Quantity>5</Quantity>  
      <Price>4.95</Price>  
    </Data>  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>66.00</Price>  
    </Data>  
    <Data>  
      <Quantity>15</Quantity>  
      <Price>29.00</Price>  
    </Data>  
  </Group>  
  <Group ID="B">  
    <Data>  
      <Quantity>1</Quantity>  
      <Price>89.99</Price>  
    </Data>  
    <Data>  
      <Quantity>10</Quantity>  
      <Price>.99</Price>  
    </Data>  
    <Data>  
      <Quantity>8</Quantity>  
      <Price>6.99</Price>  
    </Data>  
  </Group>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae406-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae406-108">See Also</span></span>  
 [<span data-ttu-id="ae406-109">Gelişmiş sorgu teknikler (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae406-109">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
