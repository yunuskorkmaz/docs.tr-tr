---
title: XPath ve LINQ to XML2 karşılaştırması
ms.date: 07/20/2015
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: 64860ab538105e7e3826b29f83b8e713ca525e21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326439"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>XPath ve LINQ-XML karşılaştırması
XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bazı benzer bir işlevsellik sağlar. Her ikisi de bu tür sonuçları öğe koleksiyonunu özniteliklerin bir koleksiyonu düğümlerinin bir koleksiyonu veya bir öğe veya öznitelik değeri olarak döndüren bir XML ağacı sorgulamak için kullanılabilir. Ancak, aynı zamanda bazı farklar vardır.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>XML XPath ve LINQ arasındaki farklar  
 XPath yeni türleri projeksiyon izin vermiyor. Bunu yalnızca düğümlerin koleksiyonları ağacından ancak döndürebilir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu yürütme ve bir nesne grafiğinin veya yeni bir şekil XML ağacında proje. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorguları kapsayan çok daha fazla işlevsellik ve XPath ifadeleri çok daha güçlü.  
  
 XPath ifadeleri yalıtım dize içinde yer alır. C# Derleyici derleme zamanında XPath ifadesi ayrıştırma yardımcı olamaz. Bunun aksine, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorguları ayrıştırılır ve C# Derleyici tarafından derlenir. Derleyici birçok sorgu hatalarını yakalama yapabiliyor.  
  
 XPath sonuçları kesin türü belirtilmiş değil. Çeşitli koşullar, bir XPath ifadesi değerlendirme sonucunu bir nesne ve uygun türde belirlemek ve sonucu gerekli olarak dönüştürmek için geliştirici kadar olur. Karşıtlık, gelen tahminleri tarafından bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu kesin türü belirtilmiş.  
  
## <a name="result-ordering"></a>Sıralama sonucu  
 XPath 1.0 öneri XPath ifadesi değerlendirme sonucu olan bir koleksiyon düzenlenmemiş olduğunu belirtir.  
  
 Ancak, ne zaman bir koleksiyon yineleme tarafından döndürülen bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XPath eksen yöntemi, koleksiyon içindeki düğümlerin belge sırayla döndürülür. Bu XPath eksenleri bile erişirken burada koşulları ters belge sipariş bakımından gibi belirtilmiştir durumda `preceding` ve `preceding-sibling`.  
  
 Karşıtlık, çoğu tarafından [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eksenleri dönüş koleksiyonları belge sipariş, ancak bunları ikilisi <xref:System.Xml.Linq.XNode.Ancestors%2A> ve <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, koleksiyonları ters belge sırada döndürür. Aşağıdaki tabloda, eksenleri numaralandırır ve her koleksiyon sırasını gösterir:  
  
|LINQ-XML ekseni|Sıralama|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Belge Sırası|  
|XContainer.Descendants|Belge Sırası|  
|XContainer.Elements|Belge Sırası|  
|XContainer.Nodes|Belge Sırası|  
|XContainer.NodesAfterSelf|Belge Sırası|  
|XContainer.NodesBeforeSelf|Belge Sırası|  
|XElement.AncestorsAndSelf|Belge tersine|  
|XElement.Attributes|Belge Sırası|  
|XElement.DescendantNodesAndSelf|Belge Sırası|  
|XElement.DescendantsAndSelf|Belge Sırası|  
|XNode.Ancestors|Belge tersine|  
|XNode.ElementsAfterSelf|Belge Sırası|  
|XNode.ElementsBeforeSelf|Belge Sırası|  
|XNode.NodesAfterSelf|Belge Sırası|  
|XNode.NodesBeforeSelf|Belge Sırası|  
  
## <a name="positional-predicates"></a>Konumsal koşulları  
 İçinde bir XPath ifadesi konumsal koşulları birçok eksen için belge sırası bakımından ifade edilir, ancak ters belge sırada olan ters eksenlerin ifade `preceding`, `preceding-sibling`, `ancestor`, ve `ancestor-or-self`. Örneğin, XPath ifadesi `preceding-sibling::*[1]` hemen önceki eşdüzey öğeyi döndürür. Nihai sonuç kümesi Belge düzeninde sunulan olsa bile bu geçerlidir.  
  
 Bunun aksine, tüm konumsal koşullarında LINQ-XML her zaman eksen sırasını cinsinden ifade edilir. Örneğin, `anElement.ElementsBeforeSelf().ToList()[0]` değil hemen önceki eşdüzey sorgulanan öğenin üst öğesinin ilk alt öğesini döndürür. Başka bir örnek: `anElement.Ancestors().ToList()[0]` üst öğesini döndürür.  
  
 Yukarıdaki yaklaşım tüm koleksiyon gerçeğe unutmayın. Bu, sorgu yazmak için en verimli şekilde değildir. Bu şekilde konumsal koşulları davranışını göstermek için yazılmıştır. Aynı sorgu yazmak için daha uygun bir yol <xref:System.Linq.Enumerable.First%2A> şekilde yöntemi: `anElement.ElementsBeforeSelf().First()`.  
  
 Hemen önceki öğesinde bulmak istiyorsanız [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], aşağıdaki ifadeyi yazarsınız:  
  
 `ElementsBeforeSelf().Last()`  
  
## <a name="performance-differences"></a>Performans farklar  
 XPath işlevindeki kullanan XPath sorguları [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gerçekleştirmez yanı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.  
  
## <a name="comparison-of-composition"></a>Birleşim karşılaştırması  
 Oluşumunu bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] çok farklı rağmen sözdiziminde sorgu biraz XPath ifadesi bir bileşimi için paralel.  
  
 Adlı bir değişkende bir öğe varsa, örneğin, `customers`, ve adlı en alt öğe bulmak istediğiniz `CompanyName` adlı tüm alt öğelerini altında `Customer`, bir XPath ifadesi gibi yazarsınız:  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName");  
```  
  
 Eşdeğer [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu:  
  
```csharp  
customers.Element("Customer").Elements("CompanyName");  
```  
  
 Her XPath eksenleri benzer parallels vardır.  
  
|XPath eksen|LINQ-XML ekseni|  
|----------------|----------------------|  
|Alt (varsayılan ekseni)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Üst (.)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|öznitelik eksen (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|üst eksen|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|üst-or-self eksen|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|descendant axis (/ /)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|descendant-or-self|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|Aşağıdaki eşdüzey|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|Önceki eşdüzey|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|Aşağıdaki|Doğrudan eşdeğeri yok.|  
|önceki|Doğrudan eşdeğeri yok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML XPath kullanıcıların (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
