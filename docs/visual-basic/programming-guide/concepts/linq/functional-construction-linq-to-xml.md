---
title: İşlevsel oluşturma (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: 03a5d7468944cfa6d6ad01dfe0e174b1e3d6ac79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717395"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="f3beb-102">İşlevsel oluşturma (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3beb-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f3beb-103">adlı XML öğeleri oluşturmak için güçlü bir yol sağlar *işlevsel oluşturma*.</span><span class="sxs-lookup"><span data-stu-id="f3beb-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="f3beb-104">Tek bir deyimde bir XML ağacı oluşturma olanağı işlevsel yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="f3beb-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="f3beb-105">Birkaç temel özellikleri vardır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel oluşturma sağlayan bir programlama arabirimi:</span><span class="sxs-lookup"><span data-stu-id="f3beb-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="f3beb-106"><xref:System.Xml.Linq.XElement> Oluşturucusu, çeşitli içerik için bağımsız değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="f3beb-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="f3beb-107">Örneğin, başka bir geçirebilirsiniz <xref:System.Xml.Linq.XElement> bir alt öğesi olan nesne.</span><span class="sxs-lookup"><span data-stu-id="f3beb-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="f3beb-108">Geçirebilirsiniz bir <xref:System.Xml.Linq.XAttribute> öğesinin bir özniteliği olan nesne.</span><span class="sxs-lookup"><span data-stu-id="f3beb-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="f3beb-109">Veya başka türde bir nesne bir dizeye dönüştürülür ve öğenin metin içeriğini olur geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3beb-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="f3beb-110"><xref:System.Xml.Linq.XElement> Oluşturucusu alır bir `params` türünde dizi <xref:System.Object>, böylece herhangi bir sayıda nesneleri için oluşturucu geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3beb-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="f3beb-111">Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3beb-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="f3beb-112">Bir nesne uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>, koleksiyon nesnesi içinde listelenmiş ve koleksiyondaki tüm öğelerin eklenir.</span><span class="sxs-lookup"><span data-stu-id="f3beb-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="f3beb-113">Koleksiyon içeriyorsa <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler, koleksiyondaki her öğe ayrı olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="f3beb-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="f3beb-114">Sonuçlarını geçirmenize izin verdiğinden, bu önemli bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Sorgu Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="f3beb-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="f3beb-115">Bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f3beb-115">The following is an example:</span></span>  
  
 <span data-ttu-id="f3beb-116">Bu özellikler bir XML ağacı oluşturmak için ve ayrıca sonuçları kullanan kod yazmak için XML değişmez değerlerini kullanarak kod yazmanıza olanak verir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular bir XML ağacı oluşturduğunuzda:</span><span class="sxs-lookup"><span data-stu-id="f3beb-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree:</span></span>  
  
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
  
 <span data-ttu-id="f3beb-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f3beb-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3beb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3beb-118">See also</span></span>
- [<span data-ttu-id="f3beb-119">XML ağaçları (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="f3beb-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
