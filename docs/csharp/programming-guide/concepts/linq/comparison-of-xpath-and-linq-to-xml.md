---
title: XPath ile LINQ to XML karşılaştırması
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e27fbe2c45e331a90261da3c0c575f1a472db88f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087384"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>XPath ile LINQ to XML karşılaştırması
XPath ile LINQ to XML benzer bir işlevsellik sağlar. Her ikisi de öğelerinin bir koleksiyonunu, özniteliklerin bir koleksiyonu, düğümlerin koleksiyonunu veya bir öğe veya öznitelik değeri olarak böyle sonuçları döndüren bir XML ağacı sorgulamak için kullanılabilir. Ancak, aynı zamanda bazı farklar vardır.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>XML için XPath ile LINQ arasındaki farklar  
 XPath yeni tür projeksiyonu izin vermez. LINQ to XML bir sorgu yürütme ve bir nesne grafiğinin ya da yeni bir şekil içinde bir XML ağacı proje, düğüm koleksiyonlarının ağacından yalnızca döndürebilir. LINQ to XML sorgularında kapsayabilir ve çok daha fazla işlevsellik ve XPath ifadeleri çok daha güçlü.  
  
 XPath ifadeleri bir dize içinde yalıtımı yok. C# Derleyici derleme zamanında XPath ifadesi ayrıştırılamıyor yardımcı olamaz. Bunun aksine, LINQ to XML sorgularında ayrıştırılır ve C# derleyicisi tarafından derlenir. Derleyici, çok sayıda sorgu hataları yakaladığınızdan kuramıyor.  
  
 XPath sonuçları kesin türlü yapılır değil. Koşullar sayısı, bir XPath ifadesi değerlendirme sonucu bir nesnedir ve uygun türde belirlemek ve sonucu gerekli olarak atama için geliştirici kadar olan. Buna karşılık gelen bir LINQ projeksiyonlar XML sorgusu için kesin türlü yapılır.  
  
## <a name="result-ordering"></a>Sıralama neden  
 XPath 1.0 öneri, bir XPath ifadesi değerlendirme sonucu olan bir koleksiyon sırasız olduğunu belirtir.  
  
 Ancak, XPath XML eksen yöntemi bir LINQ tarafından döndürülen bir koleksiyon üzerinden yineleme yapma, koleksiyon düğümleri Belge düzeninde döndürülür. Bu XPath eksenleri bile erişirken burada doğrulamaları ters belge sırayla açısından, gibi ifade edilir durumda `preceding` ve `preceding-sibling`.  
  
 Belge sırada ancak iki tanesi, LINQ to XML eksenleri çoğunu koleksiyonları aksine, iade <xref:System.Xml.Linq.XNode.Ancestors%2A> ve <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, belge ters sırada koleksiyonlarını döndürür. Aşağıdaki tabloda, eksen numaralandırır ve her koleksiyon sırasını gösterir:  
  
|LINQ to XML eksen|Sıralama|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Belge sırada|  
|XContainer.Descendants|Belge sırada|  
|XContainer.Elements|Belge sırada|  
|XContainer.Nodes|Belge sırada|  
|XContainer.NodesAfterSelf|Belge sırada|  
|XContainer.NodesBeforeSelf|Belge sırada|  
|XElement.AncestorsAndSelf|Ters belge sırayla|  
|XElement.Attributes|Belge sırada|  
|XElement.DescendantNodesAndSelf|Belge sırada|  
|XElement.DescendantsAndSelf|Belge sırada|  
|XNode.Ancestors|Ters belge sırayla|  
|XNode.ElementsAfterSelf|Belge sırada|  
|XNode.ElementsBeforeSelf|Belge sırada|  
|XNode.NodesAfterSelf|Belge sırada|  
|XNode.NodesBeforeSelf|Belge sırada|  
  
## <a name="positional-predicates"></a>Konumsal doğrulamaları  
 Bir XPath ifadesi içinde konumsal koşullar açısından birçok eksenleri için belge sırada ifade edilir, ancak olan ters eksenleri ters belge sırayla ifade `preceding`, `preceding-sibling`, `ancestor`, ve `ancestor-or-self`. Örneğin, XPath ifadesi `preceding-sibling::*[1]` hemen önceki eşdüzey öğeyi döndürür. Son sonuç kümesi belge sırada sunulur olsa bile bu durum geçerlidir.  
  
 Bunun aksine, tüm konumsal koşullarda LINQ to XML eksen sırası açısından her zaman ifade edilir. Örneğin, `anElement.ElementsBeforeSelf().ElementAt(0)` değil önceki eşdüzeyi sorgulanan öğenin üst ilk alt öğesini döndürür. Başka bir örnek: `anElement.Ancestors().ElementAt(0)` üst öğesini döndürür.  
  
 LINQ to XML hemen önceki öğeyi bulmak istiyorsanız, aşağıdaki ifade'ı yazmalısınız:  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a>Performans farkları  
 LINQ to XML XPath işlevleri kullanın XPath sorguları, XML sorgularında LINQ yanı sıra gerçekleştirmez.  
  
## <a name="comparison-of-composition"></a>Birleşim karşılaştırması  
 Bir LINQ to XML sorgusu söz dizimi içinde çok farklı olsa bir XPath ifadesi, oluşumunu için biraz paralel bileşimiyse.  
  
 Örneğin, bir öğenin adlı bir değişkende varsa `customers`, ve adlı en alt öğe bulmak istediğiniz `CompanyName` adlı tüm alt öğeleri altında `Customer`, bir XPath ifadesi şu şekilde yazmalısınız:  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 Eşdeğer LINQ to XML sorgu aşağıdaki gibidir:  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 Her bir XPath eksenleri için benzer parallels vardır.  
  
|XPath eksen|LINQ to XML eksen|  
|----------------|----------------------|  
|Alt (varsayılan eksen)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Üst (.)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|öznitelik eksen (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|üst öğe ekseni|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|üst veya self ekseni|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|alt eksen (/ /)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|alt öğesi veya kendi kendine|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|Aşağıdaki eşdüzey|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|Önceki eşdüzey|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|Aşağıdaki|Doğrudan eşdeğeri.|  
|önceki|Doğrudan eşdeğeri.|  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [LINQ to XML için XPath kullanıcıları (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
