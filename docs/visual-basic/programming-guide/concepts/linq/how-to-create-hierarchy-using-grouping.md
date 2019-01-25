---
title: 'Nasıl yapılır: (Visual Basic) gruplandırma kullanarak hiyerarşi oluşturma'
ms.date: 07/20/2015
ms.assetid: 4eb3ca6b-1aed-43de-b8b9-41c769c993f8
ms.openlocfilehash: d7c77d0e6b67f21d9d6e0ca270874641011e5924
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521003"
---
# <a name="how-to-create-hierarchy-using-grouping-visual-basic"></a><span data-ttu-id="9560c-102">Nasıl yapılır: (Visual Basic) gruplandırma kullanarak hiyerarşi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9560c-102">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>
<span data-ttu-id="9560c-103">Bu örnek verileri gruplandırmak ve ardından XML gruplandırma işlemine göre nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="9560c-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9560c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9560c-104">Example</span></span>  
 <span data-ttu-id="9560c-105">Bu örnekte ilk grupları verileri bir kategoriye göre ardından gruplandırma içinde XML hiyerarşisini yansıtır yeni bir XML dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9560c-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="9560c-106">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Sayısal veriler (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9560c-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9560c-107">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9560c-107">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9560c-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9560c-108">See also</span></span>
- [<span data-ttu-id="9560c-109">Gelişmiş sorgu teknikleri (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9560c-109">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
