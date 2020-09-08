---
title: XPath ve LINQ to XML karşılaştırması-LINQ to XML
description: Hem XPath hem de LINQ to XML sorguları, XML ağaçlarını sorgulayabilir. Bu makaleler iki seçeneği karşılaştırır ve LINQ to XML sorguları, daha güçlü, çok yönlü, daha hızlı, daha güvenli ve daha kolay bir seçim olacak şekilde bulur.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: b98651ffd7e0df0057164f40bedbc43d654d8c81
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553398"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>XPath ile LINQ to XML Karşılaştırması

XPath ve LINQ to XML bazı yollarla benzerdir. Her ikisi de bir XML ağacını sorgulamak için, bir öğe koleksiyonu, bir öznitelik koleksiyonu, bir düğüm koleksiyonu veya bir öğe ya da öznitelik değeri olarak döndürülüyor. Ancak, iki seçenek arasında önemli farklılıklar vardır.

## <a name="differences-between-xpath-and-linq-to-xml"></a>XPath ve LINQ to XML arasındaki farklar

XPath, yeni türlerin projeksiyonunu izin vermez. Yalnızca ağaçtan düğüm koleksiyonları döndürebilir, LINQ to XML bir sorgu yürütebilir ve bir nesne grafiğini ya da bir XML ağacını yeni bir şekilde proje olarak kullanabilir. LINQ to XML sorguları, XPath ifadelerinden çok daha fazlasını yapabilir.

XPath ifadeleri bir dize içinde yalıtımda mevcuttur. C# derleyicisi, derleme zamanında XPath ifadesinin ayrıştırmasına yardımcı olamaz. Bunun aksine, LINQ to XML sorguları C# derleyicisi tarafından ayrıştırılır ve derlenir. Derleyici birçok sorgu hatasını yakalayabilir.

XPath sonuçları kesin olarak yazılmamış. Bir dizi koşulda, bir XPath ifadesinin hesaplanmasının sonucu bir nesnedir ve uygun türü tespit etmek ve sonucu gerektiği şekilde dönüştürmek için geliştiriciye de sahip olur. Buna karşılık, bir LINQ to XML sorgusunun tahminleri kesin bir şekilde türdedir.

## <a name="result-ordering"></a>Sonuç sıralaması

XPath 1,0 önerisi, bir XPath ifadesinin hesaplanmasının sonucu olan bir koleksiyonun sırasız olduğunu belirtir.

Ancak, bir LINQ to XML XPath eksen yöntemi tarafından döndürülen bir koleksiyon üzerinden yineleme yaparken, koleksiyondaki düğümler belge sırasıyla döndürülür. Bu durum, koşulların, ve gibi tersine belge sırası açısından ifade edildiği XPath eksenlerine erişirken bile olur `preceding` `preceding-sibling` .

Buna karşılık, LINQ to XML eksenlerinin çoğu koleksiyonları belge sırasıyla geri döndürür. Ancak, ve iki tane, <xref:System.Xml.Linq.XNode.Ancestors%2A> ve <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> , koleksiyonları ters belge sırasıyla geri döndürür. Aşağıdaki tabloda eksenleri numaralandırılır ve her biri için koleksiyon sırası belirtilir:

|LINQ to XML ekseni|Sıralama|
|----------------------|--------------|
|XContainer. DescendantNodes|Belge sırası|
|XContainer. bağımlıları|Belge sırası|
|XContainer. Elements|Belge sırası|
|XContainer. Nodes|Belge sırası|
|XContainer. NodesAfterSelf|Belge sırası|
|XContainer. NodesBeforeSelf|Belge sırası|
|XElement. AncestorsAndSelf|Belge sırasını ters çevir|
|XElement. Attributes|Belge sırası|
|XElement. DescendantNodesAndSelf|Belge sırası|
|XElement. DescendantsAndSelf|Belge sırası|
|XNode. öncüleri|Belge sırasını ters çevir|
|XNode. ElementsAfterSelf|Belge sırası|
|XNode. ElementsBeforeSelf|Belge sırası|
|XNode. NodesAfterSelf|Belge sırası|
|XNode. NodesBeforeSelf|Belge sırası|

## <a name="positional-predicates"></a>Konumsal koşullar

Bir XPath ifadesinde konumsal koşullar, birçok eksen için belge sırası açısından ifade edilir, ancak ters eksenler için ters belge sırasıyla ifade edilir. Ters eksenler: `preceding` , `preceding-sibling` , `ancestor` , ve `ancestor-or-self` . Örneğin, XPath ifadesi `preceding-sibling::*[1]` hemen önceki eşdüzey öğeyi döndürür. Bu durum, son sonuç kümesi belge sırasıyla sunulsa bile olur.

Bunun aksine, LINQ to XML tüm konumsal koşullar her zaman eksenin sırası açısından ifade edilir. Örneğin, `anElement.ElementsBeforeSelf().ElementAt(0)` önceki eşdüzey öğeyi değil, sorgulanan öğenin üst öğesinin ilk alt öğesini döndürür. Başka bir örnek: `anElement.Ancestors().ElementAt(0)` üst öğeyi döndürür.

LINQ to XML hemen önceki öğeyi bulmak isterseniz, aşağıdaki ifadeyi yazarsınız:

```csharp
ElementsBeforeSelf().Last()
```

```vb
ElementsBeforeSelf().Last()
```

## <a name="performance-differences"></a>Performans farkları

LINQ to XML XPath işlevini kullanan XPath sorguları LINQ to XML sorgulardan daha yavaş olacaktır.

## <a name="comparison-of-composition"></a>Birleşim karşılaştırması

Bir LINQ to XML sorgusunun bileşimi bir XPath ifadesinin kompozisyonine benzerdir, ancak söz dizimi çok farklıdır.

Örneğin, adlı bir değişkende bir öğe varsa `customers` ve adlı tüm alt öğeler altında adlı bir alt öğe bulmak istiyorsanız `CompanyName` `Customer` , Bu XPath ifadesini yazarsınız:

```csharp
customers.XPathSelectElements("./Customer/CompanyName")
```

```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

Eşdeğer LINQ to XML sorgusu:

```csharp
customers.Elements("Customer").Elements("CompanyName")
```

```vb
customers.Elements("Customer").Elements("CompanyName")
```

Her XPath eksenine ilişkin benzer paraleller vardır.

|XPath ekseni|LINQ to XML ekseni|
|----------------|----------------------|
|alt öğe (varsayılan eksen)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|
|Üst (..)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|
|öznitelik ekseni (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|
|üst öğe ekseni|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|
|üst veya-kendi ekseni|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|
|alt eksen (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|
|descendant-or-self|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|
|aşağıdaki-eşdüzey|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|
|önceki eşdüzey|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> veya<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|
|Sonraki|Doğrudan eşdeğer olmaz.|
|SCRIPT|Doğrudan eşdeğer olmaz.|
