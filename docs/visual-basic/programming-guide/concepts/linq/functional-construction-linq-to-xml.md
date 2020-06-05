---
title: İşlevsel Oluşturma (LINQ to XML) Karşılaştırması
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: f42cd6f31134c5f4c7d6a75f38997b2be0c317f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398070"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="04408-102">İşlevsel oluşturma (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04408-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="04408-103">*işlevsel oluşturma*adlı XML öğeleri oluşturmak için güçlü bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="04408-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="04408-104">İşlevsel oluşturma, tek bir bildirimde bir XML ağacı oluşturma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="04408-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="04408-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Programlama arabiriminin işlevsel oluşturmayı etkinleştiren birkaç temel özelliği vardır:</span><span class="sxs-lookup"><span data-stu-id="04408-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="04408-106"><xref:System.Xml.Linq.XElement>Oluşturucu içerik için çeşitli bağımsız değişken türlerini alır.</span><span class="sxs-lookup"><span data-stu-id="04408-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="04408-107">Örneğin, <xref:System.Xml.Linq.XElement> bir alt öğe haline gelen başka bir nesneyi geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04408-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="04408-108"><xref:System.Xml.Linq.XAttribute>Öğesinin bir özniteliği haline gelen bir nesneyi geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04408-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="04408-109">Ya da bir dizeye dönüştürülen ve öğenin metin içeriği haline gelen başka herhangi bir nesne türünü geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04408-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="04408-110"><xref:System.Xml.Linq.XElement>Oluşturucuya `params` <xref:System.Object> herhangi bir sayıda nesne geçirebilmeniz için Oluşturucu türünde bir dizi alır.</span><span class="sxs-lookup"><span data-stu-id="04408-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="04408-111">Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="04408-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="04408-112">Bir nesne uygularsa <xref:System.Collections.Generic.IEnumerable%601> , nesne içindeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir.</span><span class="sxs-lookup"><span data-stu-id="04408-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="04408-113">Koleksiyon <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı ayrı eklenir.</span><span class="sxs-lookup"><span data-stu-id="04408-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="04408-114">Bir LINQ sorgusunun sonuçlarını oluşturucuya geçirmenize izin sağladığından bu önemlidir.</span><span class="sxs-lookup"><span data-stu-id="04408-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="04408-115">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="04408-115">The following is an example:</span></span>  
  
 <span data-ttu-id="04408-116">Bu özellikler, XML ağacı oluşturmak için XML değişmez değerleri kullanarak kod yazmanızı ve ayrıca bir XML ağacı oluştururken LINQ sorgularının sonuçlarını kullanan kodu yazmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="04408-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of LINQ queries when you create an XML tree:</span></span>  
  
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
  
 <span data-ttu-id="04408-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="04408-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04408-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04408-118">See also</span></span>

- [<span data-ttu-id="04408-119">XML ağaçları oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04408-119">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
