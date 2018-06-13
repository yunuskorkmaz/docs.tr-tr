---
title: 'Nasıl yapılır: Bul Descendants belirli öğe adına (C#)'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: f95551f0c1506a56474d497622b90090cc4c8865
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320238"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="1bf32-102">Nasıl yapılır: Bul Descendants belirli öğe adına (C#)</span><span class="sxs-lookup"><span data-stu-id="1bf32-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="1bf32-103">Bazen belirli bir ada sahip tüm bağımlı öğelerini bulmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="1bf32-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="1bf32-104">Tüm alt öğeleri yinelemek için kod yazma, ancak kullanmayı daha kolay <xref:System.Xml.Linq.XContainer.Descendants%2A> ekseni.</span><span class="sxs-lookup"><span data-stu-id="1bf32-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bf32-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bf32-105">Example</span></span>  
 <span data-ttu-id="1bf32-106">Aşağıdaki örnek, alt öğeleri öğenin adına göre bulmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1bf32-106">The following example shows how to find descendants based on the element name.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
IEnumerable<string> textSegs =  
    from seg in root.Descendants("t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="1bf32-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1bf32-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="1bf32-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bf32-108">Example</span></span>  
 <span data-ttu-id="1bf32-109">Aşağıdaki örnek bir ad alanı XML aynı sorgu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1bf32-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="1bf32-110">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="1bf32-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root xmlns='http://www.adatum.com'>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<string> textSegs =  
    from seg in root.Descendants(ad + "t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="1bf32-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1bf32-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bf32-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf32-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A>  
 [<span data-ttu-id="1bf32-113">Temel sorgu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1bf32-113">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
