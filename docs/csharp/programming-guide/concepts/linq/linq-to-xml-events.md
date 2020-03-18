---
title: LINQ - XML Olayları (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 8e0cb4519dd0fc2bed443d9a62b9a2545d10e161
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253168"
---
# <a name="linq-to-xml-events-c"></a>LINQ - XML Olayları (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]olaylar, bir XML ağacı değiştirildiğinde bilgilendirilmenizi sağlar.  
  
 Herhangi bir örneğine olaylar <xref:System.Xml.Linq.XObject>ekleyebilirsiniz. Olay işleyicisi daha sonra bu <xref:System.Xml.Linq.XObject> ve onun torunları herhangi bir değişiklik için olaylar alırsınız. Örneğin, ağacın köküne bir olay işleyicisi ekleyebilir ve bu olay işleyicisinden ağaca yapılan tüm değişiklikleri işleyebilirsiniz.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Olay örnekleri için <xref:System.Xml.Linq.XObject.Changing> bkz. <xref:System.Xml.Linq.XObject.Changed>  
  
## <a name="types-and-events"></a>Türleri ve Etkinlikler  
 Olaylarla çalışırken aşağıdaki türleri kullanırsınız:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Bir olay için yükseltildiğinde olay türünü <xref:System.Xml.Linq.XObject>belirtir.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Olaylar <xref:System.Xml.Linq.XObject.Changing> ve olaylar <xref:System.Xml.Linq.XObject.Changed> için veri sağlar.|  
  
 Bir XML ağacını değiştirdiğinizde aşağıdaki olaylar yükseltilir:  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Şu <xref:System.Xml.Linq.XObject> ya da onun soyundan herhangi biri değişmeden hemen önce meydana gelir.|  
|<xref:System.Xml.Linq.XObject.Changed>|Bir <xref:System.Xml.Linq.XObject> değişti veya onun torunlarından herhangi biri değişti oluşur.|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Olaylar, bir XML ağacında bazı toplu bilgileri korumak istediğinizde yararlıdır. Örneğin, faturanın satır maddelerinin toplamı olan bir fatura toplamını korumak isteyebilirsiniz. Bu örnek, karmaşık öğe `Items`altında tüm alt öğelerin toplamını korumak için olayları kullanır.  
  
### <a name="code"></a>Kod  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Total", "0"),  
    new XElement("Items")  
);  
XElement total = root.Element("Total");  
XElement items = root.Element("Items");  
items.Changed += (object sender, XObjectChangeEventArgs cea) =>  
{  
    switch (cea.ObjectChange)  
    {  
        case XObjectChange.Add:  
            if (sender is XElement)  
                total.Value = ((int)total + (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();  
            break;  
        case XObjectChange.Remove:  
            if (sender is XElement)  
                total.Value = ((int)total - (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();  
            break;  
    }  
    Console.WriteLine("Changed {0} {1}",  
      sender.GetType().ToString(), cea.ObjectChange.ToString());  
};  
items.SetElementValue("Item1", 25);  
items.SetElementValue("Item2", 50);  
items.SetElementValue("Item2", 75);  
items.SetElementValue("Item3", 133);  
items.SetElementValue("Item1", null);  
items.SetElementValue("Item4", 100);  
Console.WriteLine("Total:{0}", (int)total);  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a>Yorumlar  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```output  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  