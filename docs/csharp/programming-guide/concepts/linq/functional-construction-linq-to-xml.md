---
title: İşlevsel oluşturma (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635762"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="367fa-102">İşlevsel oluşturma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="367fa-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="367fa-103">*işlevsel oluşturma*adlı XML öğeleri oluşturmak için güçlü bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="367fa-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="367fa-104">İşlevsel oluşturma, tek bir bildirimde bir XML ağacı oluşturma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="367fa-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="367fa-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabiriminin işlevsel oluşturmayı etkinleştiren birkaç temel özelliği vardır:</span><span class="sxs-lookup"><span data-stu-id="367fa-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="367fa-106"><xref:System.Xml.Linq.XElement> Oluşturucu içerik için çeşitli bağımsız değişken türlerini alır.</span><span class="sxs-lookup"><span data-stu-id="367fa-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="367fa-107">Örneğin, bir alt öğe haline gelen başka bir <xref:System.Xml.Linq.XElement> nesnesini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="367fa-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="367fa-108">Öğesinin bir özniteliği haline gelen bir <xref:System.Xml.Linq.XAttribute> nesnesini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="367fa-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="367fa-109">Ya da bir dizeye dönüştürülen ve öğenin metin içeriği haline gelen başka herhangi bir nesne türünü geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="367fa-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="367fa-110"><xref:System.Xml.Linq.XElement> Oluşturucu <xref:System.Object>türünde bir `params` dizisi alır, böylece oluşturucuya herhangi bir sayıda nesne geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="367fa-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="367fa-111">Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="367fa-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="367fa-112">Bir nesne <xref:System.Collections.Generic.IEnumerable%601>uygularsa, nesnedeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir.</span><span class="sxs-lookup"><span data-stu-id="367fa-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="367fa-113">Koleksiyon <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="367fa-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="367fa-114">Bir LINQ sorgusunun sonuçlarını oluşturucuya geçirmenize izin sağladığından bu önemlidir.</span><span class="sxs-lookup"><span data-stu-id="367fa-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="367fa-115">Bu özellikler bir XML ağacı oluşturmak için kod yazmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="367fa-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="367fa-116">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="367fa-116">The following is an example:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="367fa-117">Bu özellikler ayrıca, bir XML ağacı oluştururken aşağıdaki gibi LINQ sorgularının sonuçlarını kullanan kodu yazmanızı de sağlar:</span><span class="sxs-lookup"><span data-stu-id="367fa-117">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="367fa-118">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="367fa-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  