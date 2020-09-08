---
title: İşlevsel oluşturma-LINQ to XML
description: LINQ to XML, tek bir bildirimde bir XML ağacı oluşturmanızı sağlayan işlevsel oluşturma sağlar.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: bcdc153d7f60cfb165dcb741d62b6af5c07a148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553099"
---
# <a name="functional-construction-linq-to-xml"></a><span data-ttu-id="94169-103">İşlevsel oluşturma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="94169-103">Functional construction (LINQ to XML)</span></span>

<span data-ttu-id="94169-104">LINQ to XML *işlevsel oluşturma*adlı XML öğeleri oluşturmak için güçlü bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="94169-104">LINQ to XML provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="94169-105">İşlevsel oluşturma, tek bir bildirimde bir XML ağacı oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="94169-105">Functional construction enables you to create an XML tree in a single statement.</span></span>

<span data-ttu-id="94169-106">LINQ to XML programlama arabiriminin birkaç temel özelliği işlevsel oluşturma sırasında kullanılır:</span><span class="sxs-lookup"><span data-stu-id="94169-106">Several key features of the LINQ to XML programming interface are used in functional construction:</span></span>

- <span data-ttu-id="94169-107"><xref:System.Xml.Linq.XElement>Oluşturucu içerik için çeşitli bağımsız değişken türlerini alır.</span><span class="sxs-lookup"><span data-stu-id="94169-107">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="94169-108">Örneğin, <xref:System.Xml.Linq.XElement> bir alt öğe haline gelen başka bir nesneyi geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94169-108">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="94169-109"><xref:System.Xml.Linq.XAttribute>Öğesinin bir özniteliği haline gelen bir nesneyi geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94169-109">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="94169-110">Ya da bir dizeye dönüştürülen ve öğenin metin içeriği haline gelen başka herhangi bir nesne türünü geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94169-110">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>
- <span data-ttu-id="94169-111"><xref:System.Xml.Linq.XElement>Oluşturucuya `params` <xref:System.Object> herhangi bir sayıda nesne geçirebilmeniz için Oluşturucu türünde bir dizi alır.</span><span class="sxs-lookup"><span data-stu-id="94169-111">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="94169-112">Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="94169-112">This enables you to create an element that has complex content.</span></span>
- <span data-ttu-id="94169-113">Bir nesne uygularsa <xref:System.Collections.Generic.IEnumerable%601> , nesne içindeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir.</span><span class="sxs-lookup"><span data-stu-id="94169-113">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="94169-114">Koleksiyon <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı ayrı eklenir.</span><span class="sxs-lookup"><span data-stu-id="94169-114">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="94169-115">Bir LINQ sorgusunun sonuçlarını oluşturucuya geçirmenize izin sağladığından bu önemlidir.</span><span class="sxs-lookup"><span data-stu-id="94169-115">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>

## <a name="example-create-an-xml-tree"></a><span data-ttu-id="94169-116">Örnek: bir XML ağacı oluşturma</span><span class="sxs-lookup"><span data-stu-id="94169-116">Example: Create an XML tree</span></span>

<span data-ttu-id="94169-117">Bir XML ağacı oluşturmak için kod yazmak üzere işlevsel oluşturma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94169-117">You can use functional construction to write code to create an XML tree.</span></span> <span data-ttu-id="94169-118">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="94169-118">The following is an example:</span></span>

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

## <a name="example-create-an-xml-tree-using-linq-query-results"></a><span data-ttu-id="94169-119">Örnek: LINQ sorgu sonuçlarını kullanarak bir XML ağacı oluşturma</span><span class="sxs-lookup"><span data-stu-id="94169-119">Example: Create an XML tree using LINQ query results</span></span>

<span data-ttu-id="94169-120">Bu özellikler, aşağıdaki örnekte olduğu gibi bir XML ağacı oluştururken LINQ sorgularının sonuçlarını kullanan kodu yazmanızı de sağlar:</span><span class="sxs-lookup"><span data-stu-id="94169-120">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as in the following example:</span></span>

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

<span data-ttu-id="94169-121">Visual Basic, XML değişmez değerleri ile aynı şey gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="94169-121">In Visual Basic, the same thing is accomplished with XML literals:</span></span>

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where CInt(el) > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

<span data-ttu-id="94169-122">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="94169-122">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="94169-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94169-123">See also</span></span>

- [<span data-ttu-id="94169-124">C 'de XML ağaçları oluşturma #</span><span class="sxs-lookup"><span data-stu-id="94169-124">Create XML Trees in C#</span></span>](create-xml-trees.md)
- [<span data-ttu-id="94169-125">Visual Basic XML sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="94169-125">XML literals in Visual Basic</span></span>](xml-literals.md)
