---
title: LINQ-XML eksenleri genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9161f151-cfa8-4408-94ba-08a9ba3a486d
ms.openlocfilehash: 9164dcff118c5fa3d15a5fe673b2174a4002e9d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-xml-axes-overview-visual-basic"></a>LINQ-XML eksenleri genel bakış (Visual Basic)
Bir XML ağacı oluşturulamadı veya bir XML ağacına bir XML belgesi yüklenemedi sonra öğeleri ve özniteliklerinin bulmak ve bunların değerleri almak için sorgulayabilirsiniz. Koleksiyonlar üzerinden almak *eksen yöntemleri*, olarak da bilinir *eksenleri*. Bazı eksenleri yöntemlerdir <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıfları bu iade <xref:System.Collections.Generic.IEnumerable%601> koleksiyonları. Eksenleri uzantı yöntemleri bazıları <xref:System.Xml.Linq.Extensions> sınıfı. Genişletme yöntemleri olarak uygulanan eksenleri koleksiyonlar üzerinde çalışır ve koleksiyon döndürür.  
  
 Bölümünde açıklandığı gibi [XElement sınıfına genel bakış](http://msdn.microsoft.com/library/d35180fe-7016-4895-9bfc-ba1e3f7875ec), bir <xref:System.Xml.Linq.XElement> nesnesi tek öğe düğümü temsil eder. Bir öğenin içeriğini (bazen yapılandırılmış içerik denir) karmaşık olabilir veya basit bir öğe olabilir. Basit bir öğe boş olabilir veya bir değer içerebilir. Düğüm yapılandırılmış içerik varsa, alt öğelerin numaralandırmalar almak için çeşitli eksen yöntemlerini kullanabilirsiniz. En yaygın kullanılan eksen yöntemleri <xref:System.Xml.Linq.XContainer.Elements%2A> ve <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
 Koleksiyonları döndürmesi eksen yöntemlere ek olarak, yaygın olarak kullanır daha fazla iki yöntem vardır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular. <xref:System.Xml.Linq.XContainer.Element%2A> Yöntem tek bir <xref:System.Xml.Linq.XElement>. <xref:System.Xml.Linq.XElement.Attribute%2A> Yöntem tek bir <xref:System.Xml.Linq.XAttribute>.  
  
 Birçok amacıyla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları bir ağaç inceleyin, veri ayıklayın ve dönüştürmek için en güçlü yol sunar. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları uygulayan nesneler üzerinde çalışan <xref:System.Collections.Generic.IEnumerable%601>ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eksen return <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> koleksiyonları ve <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XAttribute> koleksiyonları. Sorgularınızın gerçekleştirmek için bu koleksiyonları gerekir.  
  
 Öğeleri ve özniteliklerinin koleksiyonları almak eksen yöntemlere ek olarak, harika ayrıntı ağacında yinelemek izin eksen yöntemler vardır. Örneğin, öğeleri ve öznitelikleri ile ilgilenen yerine ağaç düğümleri ile çalışabilirsiniz. Düğümleri bir daha hassas ayrıntı öğeleri ve özniteliklerinin daha düzeyindedir. Düğümleri ile çalışırken, işleme yönergeleri ve daha fazla XML açıklamaları, metin düğümleri inceleyebilirsiniz. Bu işlevsellik, örneğin, sözcük işlemci yazma ve belgeleri XML olarak kaydetme istediği yapılandırabilecek önemlidir. Ancak, XML programcıları çoğunluğu öncelikle açısından öğeleri, öznitelikleri ve değerleri.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Öğe koleksiyonunu almak için yöntemleri  
 Aşağıdaki yöntemleri bir özetidir <xref:System.Xml.Linq.XElement> sınıfı (veya temel sınıflarından) üzerinde çağıran bir <xref:System.Xml.Linq.XElement> öğe koleksiyonunu döndürülecek.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Döndürür bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> üyenin üst öğelerinden oluşan bu öğe. Bir aşırı döndüren bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> üyenin belirtilen üst öğelerinden <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Döndürür bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> , bu öğenin alt öğeleri. Bir aşırı döndüren bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> belirtilen alt öğelerini <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Döndürür bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> bu öğenin alt öğelerinin. Bir aşırı döndüren bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> belirtilen alt öğelerini <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Döndürür bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> bu öğeden sonra gelen öğe. Bir aşırı döndüren bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> belirtilen öğe bu öğesinden sonra <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Döndürür bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> bu öğeden önce gelen öğe. Bir aşırı döndüren bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> belirtilen öğe bu öğe önce <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Döndürür bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> bu öğeyi ve alt öğelerinden biri. Bir aşırı döndüren bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> belirtilen öğelerin <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Döndürür bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> bu öğeyi ve alt öğeleri. Bir aşırı döndüren bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> belirtilen öğelerin <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Tek bir öğe alma yöntemi  
 Aşağıdaki yöntem tek bir alt gelen alır bir <xref:System.Xml.Linq.XElement> nesnesi.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|İlk alt öğesini döndürür <xref:System.Xml.Linq.XElement> belirtilen olan nesneyi <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Özniteliklerin bir koleksiyonu alma yöntemi  
 Aşağıdaki yöntem öznitelikleri alır bir <xref:System.Xml.Linq.XElement> nesnesi.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Döndürür bir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XAttribute> tüm öznitelikleri.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Tek bir öznitelik alma yöntemi  
 Aşağıdaki yöntem tek bir özniteliği alır bir <xref:System.Xml.Linq.XElement> nesnesi.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Döndürür <xref:System.Xml.Linq.XAttribute> belirtilen olan <xref:System.Xml.Linq.XName>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
