---
title: 'Nasıl yapılır: belirli bir öğe adına (C#) ile alt öğeleri bulma'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 6c5e035b4ee0168a0c41a34754314e18d089b1ef
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556577"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a>Nasıl yapılır: belirli bir öğe adına (C#) ile alt öğeleri bulma
Bazen belirli bir ada sahip tüm alt öğeleri bulmak istediğiniz. Tüm alt öğeleri arasında yineleme yapmak için kod yazabilirsiniz, ancak kullanmak daha kolaydır <xref:System.Xml.Linq.XContainer.Descendants%2A> ekseni.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğeyi adına göre alt öğeleri bulmak gösterilmektedir.  
  
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
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir. Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
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
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
- [Temel sorgular (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
