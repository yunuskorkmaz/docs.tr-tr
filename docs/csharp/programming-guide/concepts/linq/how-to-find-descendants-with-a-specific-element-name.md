---
title: 'Nasıl yapılır: belirli bir öğe adına (C#) ile alt öğeleri bulma'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 6c5e035b4ee0168a0c41a34754314e18d089b1ef
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861425"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="0e51a-102">Nasıl yapılır: belirli bir öğe adına (C#) ile alt öğeleri bulma</span><span class="sxs-lookup"><span data-stu-id="0e51a-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="0e51a-103">Bazen belirli bir ada sahip tüm alt öğeleri bulmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="0e51a-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="0e51a-104">Tüm alt öğeleri arasında yineleme yapmak için kod yazabilirsiniz, ancak kullanmak daha kolaydır <xref:System.Xml.Linq.XContainer.Descendants%2A> ekseni.</span><span class="sxs-lookup"><span data-stu-id="0e51a-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e51a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e51a-105">Example</span></span>  
 <span data-ttu-id="0e51a-106">Aşağıdaki örnek, öğeyi adına göre alt öğeleri bulmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0e51a-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="0e51a-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0e51a-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="0e51a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e51a-108">Example</span></span>  
 <span data-ttu-id="0e51a-109">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e51a-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="0e51a-110">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="0e51a-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="0e51a-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0e51a-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e51a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e51a-112">See Also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
- [<span data-ttu-id="0e51a-113">Temel sorgular (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0e51a-113">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
