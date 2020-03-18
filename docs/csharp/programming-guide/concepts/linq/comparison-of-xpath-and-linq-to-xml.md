---
title: XPath ile LINQ to XML Karşılaştırması
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e9bf192a2075653802f0c5a8b4e44ff0ceacb975
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66487537"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>XPath ile LINQ to XML Karşılaştırması
XPath ve LINQ XML bazı benzer işlevsellik sunuyoruz. Her ikisi de bir XML ağacını sorgulamak için kullanılabilir, öğeler topluluğu, özniteliklertopluluğu, düğümler koleksiyonu veya bir öğe nin veya öznitelik değeri gibi sonuçları döndürür. Ancak, bazı farklılıklar da vardır.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>XPath ve LINQ ile XML arasındaki farklar  
 XPath yeni türlerin projeksiyonuna izin vermez. Yalnızca ağaçtan düğüm koleksiyonlarını döndürebilir, linq'den XML'e bir sorgu yürütebilir ve bir nesne grafiği veya XML ağacını yeni bir şekilde yansıtabilir. LINQ xml sorguları çok daha fazla işlevselliği kapsar ve XPath ifadelerinden çok daha güçlüdür.  
  
 XPath ifadeleri bir dize içinde yalıtılmış olarak bulunur. C# derleyicisi, XPath ifadesini derleme zamanında ayrışdırma yardımcı olamaz. Buna karşılık, LINQ xml sorguları ayrıştı ve C # derleyici tarafından derlenir. Derleyici birçok sorgu hatasını yakalayabilir.  
  
 XPath sonuçları güçlü bir şekilde yazılmıyor. Bir dizi durumda, bir XPath ifadesini değerlendirmenin sonucu bir nesnedir ve uygun türü belirlemek ve sonucu gerektiği gibi atmak geliştiriciye katılır. Bunun aksine, bir LINQ'dan XML sorgusuna kadar olan projeksiyonlar güçlü bir şekilde yazılır.  
  
## <a name="result-ordering"></a>Sonuç Sıralama  
 XPath 1.0 Önerisi, Bir XPath ifadesini değerlendirme nin sonucu olan bir koleksiyonun sırasız olduğunu belirtir.  
  
 Ancak, bir LINQ tarafından XML XPath ekseni yöntemine döndürülen bir koleksiyon aracılığıyla yinelendiğinde, koleksiyondaki düğümler belge sırasına göre döndürülür. Bu durum, yüklemlerin ters belge sırası açısından ifade edildiği XPath eksenlerine erişirken `preceding-sibling`bile durum böyledir. `preceding`  
  
 Bunun aksine, LINQ'dan XML eksenlerine kadar olan eksenlerin çoğu <xref:System.Xml.Linq.XNode.Ancestors%2A> koleksiyonları <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>belge sırasına göre döndürer, ancak bunlardan ikisi ve koleksiyonları ters belge sırasına göre döndürer. Aşağıdaki tablo eksenleri sıralar ve her biri için toplama sırasını gösterir:  
  
|LINQ - XML ekseni|Sıralama|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Belge sırası|  
|XContainer.Descendants|Belge sırası|  
|XContainer.Elements|Belge sırası|  
|XContainer.Nodes|Belge sırası|  
|XContainer.NodesAfterSelf|Belge sırası|  
|XContainer.NodesBeforeSelf|Belge sırası|  
|xelement.atalarandself|Ters belge sırası|  
|xelement.öznitelikler|Belge sırası|  
|XElement.DescendantNodesAndSelf|Belge sırası|  
|XElement.DescendantsAndSelf|Belge sırası|  
|XNode.Atalar|Ters belge sırası|  
|XNode.ElementsAfterSelf|Belge sırası|  
|XNode.ElementsBeforeSelf|Belge sırası|  
|XNode.NodesAfterSelf|Belge sırası|  
|XNode.DüğümlerKendinden Önce|Belge sırası|  
  
## <a name="positional-predicates"></a>Pozisyonel Yüklemler  
 Bir XPath ifadesi içinde, konumsal yüklemler birçok eksen için belge sırası açısından ifade edilir, ancak ters `preceding`eksenler `ancestor`için `ancestor-or-self`ters belge sırasına göre ifade edilir, hangi , , `preceding-sibling`, ve . Örneğin, XPath ifadesi `preceding-sibling::*[1]` hemen önceki kardeş döndürür. Nihai sonuç kümesi belge sırasına göre sunulsa da durum böyledir.  
  
 Buna karşılık, LINQ'dan XML'e kadar olan tüm konumsal yüklemler her zaman eksenin sırası açısından ifade edilir. Örneğin, `anElement.ElementsBeforeSelf().ElementAt(0)` sorgulandı öğenin üst ilk alt öğesi değil, hemen önceki kardeş döndürür. Başka bir `anElement.Ancestors().ElementAt(0)` örnek: üst öğeyi döndürür.  
  
 Linq'te XML'de hemen önceki öğeyi bulmak isterseniz, aşağıdaki ifadeyi yazarsınız:  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a>Performans Farklılıkları  
 LINQ'dan XML'e XPath işlevini kullanan XPath sorguları, LINQ'dan XML sorgularına kadar performans göstermez.  
  
## <a name="comparison-of-composition"></a>Kompozisyon Karşılaştırması  
 LinQ'dan XML sorgusuna kompozisyon, sözdiziminde çok farklı olsa da, xpath ifadesinin bileşimine biraz paraleldir.  
  
 Örneğin, adlı `customers`bir değişkende bir öğeniz varsa ve tüm alt `CompanyName` öğelerin altında `Customer`adı geçen bir torun öğesi bulmak istiyorsanız, aşağıdaki gibi bir XPath ifadesi yazarsınız:  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 XML sorgusuna eşdeğer LINQ:  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 XPath eksenlerinin her biri için benzer paralellikler vardır.  
  
|XPath ekseni|LINQ - XML ekseni|  
|----------------|----------------------|  
|alt (varsayılan eksen)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Veli (..)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|öznitelik ekseni (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|ata ekseni|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|ata ya da benlik ekseni|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|soyundan gelen eksen (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|soyundan gelen ya da kendi kendine|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|aşağıdaki kardeş|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|önceki kardeş|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|Aşağıdaki|Doğrudan eşdeğeri yok.|  
|Önceki|Doğrudan eşdeğeri yok.|  
  