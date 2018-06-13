---
title: 'Nasıl yapılır: gruplandırma (C#) kullanarak hiyerarşi oluşturma'
ms.date: 07/20/2015
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
ms.openlocfilehash: 9ad9ea723a54b50c3d5b047408fce760a8f53273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327518"
---
# <a name="how-to-create-hierarchy-using-grouping-c"></a><span data-ttu-id="6e4cb-102">Nasıl yapılır: gruplandırma (C#) kullanarak hiyerarşi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6e4cb-102">How to: Create Hierarchy Using Grouping (C#)</span></span>
<span data-ttu-id="6e4cb-103">Bu örnek, verileri gruplandırmak ve XML gruplandırılması tabanlı oluşturmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6e4cb-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e4cb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e4cb-104">Example</span></span>  
 <span data-ttu-id="6e4cb-105">Bu örnek ilk grupları verileri bir kategoriye göre sonra XML hiyerarşisini gruplandırma yansıtır yeni bir XML dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e4cb-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="6e4cb-106">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: sayısal verileri (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6e4cb-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement doc = XElement.Load("Data.xml");  
var newData =  
    new XElement("Root",  
        from data in doc.Elements("Data")  
        group data by (string)data.Element("Category") into groupedData  
        select new XElement("Group",  
            new XAttribute("ID", groupedData.Key),  
            from g in groupedData  
            select new XElement("Data",  
                g.Element("Quantity"),  
                g.Element("Price")  
            )  
        )  
    );  
Console.WriteLine(newData);  
```  
  
 <span data-ttu-id="6e4cb-107">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="6e4cb-107">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e4cb-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e4cb-108">See Also</span></span>  
 [<span data-ttu-id="6e4cb-109">Gelişmiş sorgu teknikler (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6e4cb-109">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
