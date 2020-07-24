---
title: İşlevsel oluşturma (LINQ to XML) (C#)
description: LINQ to XML programlama arabiriminin, C# ' de tek bir ifadede bir XML ağacı oluşturma özelliği olan işlevsel oluşturmayı nasıl sağladığını öğrenin.
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: f209a7ef2a4597ec8eeccb3083b77223a27e7a65
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103766"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="d4159-103">İşlevsel oluşturma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d4159-103">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d4159-104">*işlevsel oluşturma*adlı XML öğeleri oluşturmak için güçlü bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4159-104">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="d4159-105">İşlevsel oluşturma, tek bir bildirimde bir XML ağacı oluşturma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="d4159-105">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="d4159-106">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Programlama arabiriminin işlevsel oluşturmayı etkinleştiren birkaç temel özelliği vardır:</span><span class="sxs-lookup"><span data-stu-id="d4159-106">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="d4159-107"><xref:System.Xml.Linq.XElement>Oluşturucu içerik için çeşitli bağımsız değişken türlerini alır.</span><span class="sxs-lookup"><span data-stu-id="d4159-107">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="d4159-108">Örneğin, <xref:System.Xml.Linq.XElement> bir alt öğe haline gelen başka bir nesneyi geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4159-108">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="d4159-109"><xref:System.Xml.Linq.XAttribute>Öğesinin bir özniteliği haline gelen bir nesneyi geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4159-109">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="d4159-110">Ya da bir dizeye dönüştürülen ve öğenin metin içeriği haline gelen başka herhangi bir nesne türünü geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4159-110">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="d4159-111"><xref:System.Xml.Linq.XElement>Oluşturucuya `params` <xref:System.Object> herhangi bir sayıda nesne geçirebilmeniz için Oluşturucu türünde bir dizi alır.</span><span class="sxs-lookup"><span data-stu-id="d4159-111">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="d4159-112">Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4159-112">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="d4159-113">Bir nesne uygularsa <xref:System.Collections.Generic.IEnumerable%601> , nesne içindeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir.</span><span class="sxs-lookup"><span data-stu-id="d4159-113">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="d4159-114">Koleksiyon <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı ayrı eklenir.</span><span class="sxs-lookup"><span data-stu-id="d4159-114">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="d4159-115">Bir LINQ sorgusunun sonuçlarını oluşturucuya geçirmenize izin sağladığından bu önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d4159-115">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="d4159-116">Bu özellikler bir XML ağacı oluşturmak için kod yazmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4159-116">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="d4159-117">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d4159-117">The following is an example:</span></span>  
  
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
  
 <span data-ttu-id="d4159-118">Bu özellikler ayrıca, bir XML ağacı oluştururken aşağıdaki gibi LINQ sorgularının sonuçlarını kullanan kodu yazmanızı de sağlar:</span><span class="sxs-lookup"><span data-stu-id="d4159-118">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="d4159-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d4159-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  