---
title: İşlevsel Oluşturma (LINQ to XML) Karşılaştırması
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: a51360d6c8d44770c462afb728a1fb78d3e2cd42
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636854"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="27dc9-102">İşlevsel oluşturma (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27dc9-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="27dc9-103">*işlevsel oluşturma*adlı XML öğeleri oluşturmak için güçlü bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="27dc9-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="27dc9-104">İşlevsel oluşturma, tek bir bildirimde bir XML ağacı oluşturma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="27dc9-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="27dc9-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabiriminin işlevsel oluşturmayı etkinleştiren birkaç temel özelliği vardır:</span><span class="sxs-lookup"><span data-stu-id="27dc9-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="27dc9-106"><xref:System.Xml.Linq.XElement> Oluşturucu içerik için çeşitli bağımsız değişken türlerini alır.</span><span class="sxs-lookup"><span data-stu-id="27dc9-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="27dc9-107">Örneğin, bir alt öğe haline gelen başka bir <xref:System.Xml.Linq.XElement> nesnesini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27dc9-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="27dc9-108">Öğesinin bir özniteliği haline gelen bir <xref:System.Xml.Linq.XAttribute> nesnesini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27dc9-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="27dc9-109">Ya da bir dizeye dönüştürülen ve öğenin metin içeriği haline gelen başka herhangi bir nesne türünü geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27dc9-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="27dc9-110"><xref:System.Xml.Linq.XElement> Oluşturucu <xref:System.Object>türünde bir `params` dizisi alır, böylece oluşturucuya herhangi bir sayıda nesne geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27dc9-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="27dc9-111">Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="27dc9-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="27dc9-112">Bir nesne <xref:System.Collections.Generic.IEnumerable%601>uygularsa, nesnedeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir.</span><span class="sxs-lookup"><span data-stu-id="27dc9-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="27dc9-113">Koleksiyon <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="27dc9-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="27dc9-114">Bir LINQ sorgusunun sonuçlarını oluşturucuya geçirmenize izin sağladığından bu önemlidir.</span><span class="sxs-lookup"><span data-stu-id="27dc9-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="27dc9-115">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="27dc9-115">The following is an example:</span></span>  
  
 <span data-ttu-id="27dc9-116">Bu özellikler, XML ağacı oluşturmak için XML değişmez değerleri kullanarak kod yazmanızı ve ayrıca bir XML ağacı oluştururken LINQ sorgularının sonuçlarını kullanan kodu yazmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="27dc9-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of LINQ queries when you create an XML tree:</span></span>  
  
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
  
 <span data-ttu-id="27dc9-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="27dc9-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27dc9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27dc9-118">See also</span></span>

- [<span data-ttu-id="27dc9-119">XML ağaçları oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27dc9-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
