---
title: Belirli bir öğe adı (C#) ile torunları bulmak için nasıl
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: b3200a2fdf75dbf52079a2b3d27aa1a88d313406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141086"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="4e575-102">Belirli bir öğe adı (C#) ile torunları bulmak için nasıl</span><span class="sxs-lookup"><span data-stu-id="4e575-102">How to find descendants with a specific element name (C#)</span></span>
<span data-ttu-id="4e575-103">Bazen belirli bir ada sahip tüm torunları bulmak istiyorum.</span><span class="sxs-lookup"><span data-stu-id="4e575-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="4e575-104">Tüm soyundan gelenler aracılığıyla yinelemek için kod yazabilirsiniz, ancak <xref:System.Xml.Linq.XContainer.Descendants%2A> ekseni kullanmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="4e575-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e575-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e575-105">Example</span></span>  
 <span data-ttu-id="4e575-106">Aşağıdaki örnek, öğe adına dayalı torunları bulmak için nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e575-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="4e575-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4e575-107">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="4e575-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e575-108">Example</span></span>  
 <span data-ttu-id="4e575-109">Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e575-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="4e575-110">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4e575-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="4e575-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4e575-111">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e575-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e575-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
