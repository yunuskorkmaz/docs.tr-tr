---
title: İşlev yapımı (LINQ-XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: c837660adf9c62c8f4304b92d37f732795c981c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329861"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="a6535-102">İşlev yapımı (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a6535-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="a6535-103"> adlı XML öğeleri oluşturmak için güçlü bir yol sağlar *işlevsel yapım*.</span><span class="sxs-lookup"><span data-stu-id="a6535-103"> provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="a6535-104">Bir XML ağacı tek bir deyimde oluşturabilme işlevsel yapıdır.</span><span class="sxs-lookup"><span data-stu-id="a6535-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="a6535-105">Birkaç temel özellikleri vardır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel yapım etkinleştirmek programlama arabirimi:</span><span class="sxs-lookup"><span data-stu-id="a6535-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="a6535-106"><xref:System.Xml.Linq.XElement> Oluşturucusu çeşitli içerik için bağımsız değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="a6535-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="a6535-107">Örneğin, başka bir geçirebilirsiniz <xref:System.Xml.Linq.XElement> bir alt öğesi olur nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a6535-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="a6535-108">Geçirebilirsiniz bir <xref:System.Xml.Linq.XAttribute> öğesinin özniteliği hale nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a6535-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="a6535-109">Veya herhangi bir dizeye dönüştürülür ve öğenin metin içeriğini olur, nesne türü geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6535-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="a6535-110"><xref:System.Xml.Linq.XElement> Oluşturucusu geçen bir `params` türünde dizi <xref:System.Object>, böylece oluşturucuya herhangi bir sayıda nesnelerini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6535-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="a6535-111">Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6535-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="a6535-112">Bir nesne uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>nesne koleksiyonunda numaralandırılan ve koleksiyondaki tüm öğeleri eklenir.</span><span class="sxs-lookup"><span data-stu-id="a6535-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="a6535-113">Koleksiyon içeriyorsa <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneleri, koleksiyondaki her öğe ayrı olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="a6535-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="a6535-114">Sonuçlarını geçirmenize olanak tanır bu önemlidir, çünkü bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu oluşturucuya.</span><span class="sxs-lookup"><span data-stu-id="a6535-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="a6535-115">Bu özellikler bir XML ağacı oluşturmak üzere kod yazmak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a6535-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="a6535-116">Bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a6535-116">The following is an example:</span></span>  
  
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
  
 <span data-ttu-id="a6535-117">Bu özellikleri de sonuçlarını kullanan kodu yazmanızı etkinleştirmek [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular ne zaman bir XML ağacı gibi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a6535-117">These features also enable you to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="a6535-118">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="a6535-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6535-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6535-119">See Also</span></span>  
 [<span data-ttu-id="a6535-120">Oluşturma XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="a6535-120">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
