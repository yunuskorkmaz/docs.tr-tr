---
title: Fonksiyonel Yapı (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635762"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="8f4ee-102">Fonksiyonel Yapı (LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8f4ee-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="8f4ee-103">*fonksiyonel yapı*adı verilen XML öğeleri oluşturmak için güçlü bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="8f4ee-104">Fonksiyonel yapı, tek bir ifadede bir XML ağacı oluşturma yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="8f4ee-105">Programlama arabiriminin [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel yapıyı etkinleştiren birkaç temel özelliği vardır:</span><span class="sxs-lookup"><span data-stu-id="8f4ee-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="8f4ee-106">Oluşturucu <xref:System.Xml.Linq.XElement> içerik için çeşitli bağımsız değişkenler alır.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="8f4ee-107">Örneğin, bir alt <xref:System.Xml.Linq.XElement> öğe olur başka bir nesne, geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="8f4ee-108">Öğenin bir <xref:System.Xml.Linq.XAttribute> özniteliği haline gelen bir nesneyi geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="8f4ee-109">Veya bir dize dönüştürülür ve öğenin metin içeriği olur nesne, başka bir tür geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="8f4ee-110">Oluşturucu, <xref:System.Xml.Linq.XElement> istediğiniz `params` sayıda <xref:System.Object>nesneyi oluşturucuya geçirebilmeniz için bir dizi tür alır.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="8f4ee-111">Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="8f4ee-112">Bir nesne uygularsa, <xref:System.Collections.Generic.IEnumerable%601>nesnedeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="8f4ee-113">Koleksiyon <xref:System.Xml.Linq.XElement> içeriyorsa <xref:System.Xml.Linq.XAttribute> veya nesnelere, koleksiyondaki her öğe ayrı olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="8f4ee-114">Bu önemlidir, çünkü bir LINQ sorgusunun sonuçlarını oluşturucuya geçirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="8f4ee-115">Bu özellikler, bir XML ağacı oluşturmak için kod yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f4ee-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="8f4ee-116">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8f4ee-116">The following is an example:</span></span>  
  
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
  
 <span data-ttu-id="8f4ee-117">Bu özellikler, bir XML ağacı oluşturduğunuzda LINQ sorgularının sonuçlarını kullanan kod yazmanızı da sağlar:</span><span class="sxs-lookup"><span data-stu-id="8f4ee-117">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="8f4ee-118">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8f4ee-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  