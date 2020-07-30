---
title: Belirli bir öğe adına sahip alt öğeleri bulma (C#)
description: Alt öğeler eksenini kullanarak belirli bir ada sahip tüm alt öğeleri bulmayı öğrenin. Kod örneklerine ve ek kaynaklara bakın.
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 96ebf2d10a9ed5e07aab2870142f9869903ad442
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303250"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="b20be-104">Belirli bir öğe adına sahip alt öğeleri bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="b20be-104">How to find descendants with a specific element name (C#)</span></span>
<span data-ttu-id="b20be-105">Bazen belirli bir ada sahip tüm alt öğeleri bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b20be-105">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="b20be-106">Tüm alt öğeler boyunca yinelemek için kod yazabilirsiniz, ancak eksenin kullanımı daha kolaydır <xref:System.Xml.Linq.XContainer.Descendants%2A> .</span><span class="sxs-lookup"><span data-stu-id="b20be-106">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b20be-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b20be-107">Example</span></span>  
 <span data-ttu-id="b20be-108">Aşağıdaki örnek, öğe adına göre alt öğelerin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b20be-108">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="b20be-109">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b20be-109">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="b20be-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b20be-110">Example</span></span>  
 <span data-ttu-id="b20be-111">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b20be-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="b20be-112">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b20be-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="b20be-113">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b20be-113">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="b20be-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b20be-114">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
