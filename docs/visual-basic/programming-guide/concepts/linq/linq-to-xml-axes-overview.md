---
title: LINQ to XML Eksenlerine Genel Bakış
ms.date: 07/20/2015
ms.assetid: 9161f151-cfa8-4408-94ba-08a9ba3a486d
ms.openlocfilehash: 47e95fcca251212475c925a24d382ba2dceedd62
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352033"
---
# <a name="linq-to-xml-axes-overview-visual-basic"></a>LINQ to XML eksenlerine genel bakış (Visual Basic)
Bir xml ağacını oluşturduktan veya bir XML ağacına bir XML belgesi yükledikten sonra, öğeleri ve öznitelikleri bulmak ve değerlerini almak için onu sorgulayabilirsiniz. Koleksiyonları, eksen olarak *da adlandırılan* *eksen yöntemleri*aracılığıyla alırsınız. Eksenlerden bazıları, <xref:System.Collections.Generic.IEnumerable%601> koleksiyonları döndüren <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıflarında yöntemlerdir. Eksenlerden bazıları <xref:System.Xml.Linq.Extensions> sınıfında uzantı yöntemleridir. Uzantı yöntemleri olarak uygulanan eksenler koleksiyonlar üzerinde çalışır ve koleksiyonlar döndürülür.  
  
 [XElement sınıfına genel bakış](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md)bölümünde açıklandığı gibi, bir <xref:System.Xml.Linq.XElement> nesnesi tek bir öğe düğümünü temsil eder. Bir öğenin içeriği karmaşık olabilir (bazen yapılandırılmış içerik olarak adlandırılır) veya basit bir öğe olabilir. Basit bir öğe boş olabilir veya bir değer içerebilir. Düğüm yapısal içerik içeriyorsa, alt öğelerin numaralandırmalar almak için çeşitli eksen yöntemlerini kullanabilirsiniz. En yaygın kullanılan eksen yöntemleri <xref:System.Xml.Linq.XContainer.Elements%2A> ve <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
 Koleksiyonları döndüren eksen yöntemlerine ek olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgularda yaygın olarak kullanabileceğiniz iki yöntem vardır. <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi tek bir <xref:System.Xml.Linq.XElement>döndürür. <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemi tek bir <xref:System.Xml.Linq.XAttribute>döndürür.  
  
 Birçok amaç için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları, bir ağacı incelemek, verileri dosyadan ayıklamak ve dönüştürmek için en güçlü yolu sağlar. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları <xref:System.Collections.Generic.IEnumerable%601>uygulayan nesneler üzerinde çalışır ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eksenleri <xref:System.Xml.Linq.XElement> koleksiyonlarının <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.Collections.Generic.IEnumerable%601> koleksiyonlarının <xref:System.Xml.Linq.XAttribute> döndürür. Sorgularınızı gerçekleştirmek için bu koleksiyonlara ihtiyacınız vardır.  
  
 Öğe ve özniteliklerin koleksiyonlarını alan eksen yöntemlerine ek olarak, ağaç üzerinde harika ayrıntılarla yineleme yapmanızı sağlayan eksen yöntemleri vardır. Örneğin, öğeleri ve öznitelikleri kullanmak yerine, ağacın düğümleri ile çalışabilirsiniz. Düğümler, öğe ve özniteliklerin daha ayrıntılı bir düzeyde ayrıntı düzeyidir. Düğümlerle çalışırken, XML açıklamalarını, metin düğümlerini, işleme talimatlarını ve daha fazlasını inceleyebilirsiniz. Bu işlevsellik, örneğin, bir sözcük işlemcisi yazan ve belgeleri XML olarak kaydetmek isteyen bir kişiye önemlidir. Ancak, XML programcılarının çoğunluğu öncelikle öğeler, öznitelikler ve değerleri ile ilgilidir.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Öğe koleksiyonunu alma yöntemleri  
 Aşağıda bir öğe koleksiyonu döndürmek için bir <xref:System.Xml.Linq.XElement> çağırdığınız <xref:System.Xml.Linq.XElement> sınıfının (veya temel sınıflarının) yöntemlerinin bir özeti verilmiştir.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Bu öğenin üst öğelerinden <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür. Aşırı yükleme, belirtilen <xref:System.Xml.Linq.XName>sahip olan üst öğelerinden <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Bu öğenin alt öğelerinin <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür. Aşırı yükleme, belirtilen <xref:System.Xml.Linq.XName>sahip alt öğelerin <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Bu öğenin alt öğelerinin <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür. Aşırı yükleme, belirtilen <xref:System.Xml.Linq.XName>sahip alt öğelerin <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Bu öğeden sonra gelen öğelerin <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür. Aşırı yükleme, belirtilen <xref:System.Xml.Linq.XName>sahip olan bu öğeden sonra gelen öğelerin <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Bu öğeden önce gelen öğelerin <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür. Aşırı yükleme, belirtilen <xref:System.Xml.Linq.XName>sahip olan bu öğeden önceki öğelerin <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Bu öğenin ve onun üst öğelerinden <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür. Aşırı yükleme, belirtilen <xref:System.Xml.Linq.XName>sahip öğelerin <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Bu öğenin ve alt öğelerinin <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür. Aşırı yükleme, belirtilen <xref:System.Xml.Linq.XName>sahip öğelerin <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> döndürür.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Tek bir öğe alma yöntemi  
 Aşağıdaki yöntem <xref:System.Xml.Linq.XElement> nesnesinden tek bir alt öğe alır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Belirtilen <xref:System.Xml.Linq.XName>sahip olan ilk alt <xref:System.Xml.Linq.XElement> nesnesini döndürür.|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Özniteliklerin koleksiyonunu alma yöntemi  
 Aşağıdaki yöntem bir <xref:System.Xml.Linq.XElement> nesnesinden öznitelikleri alır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Tüm özniteliklerin <xref:System.Xml.Linq.XAttribute> <xref:System.Collections.Generic.IEnumerable%601> döndürür.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Tek bir özniteliği alma yöntemi  
 Aşağıdaki yöntem <xref:System.Xml.Linq.XElement> nesnesinden tek bir özniteliği alır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Belirtilen <xref:System.Xml.Linq.XName>sahip <xref:System.Xml.Linq.XAttribute> döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
