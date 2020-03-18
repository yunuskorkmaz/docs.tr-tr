---
title: LINQ - XML Eksenlerine Genel Bakış (C#)
ms.date: 07/20/2015
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
ms.openlocfilehash: c8b64731925f37d54bded62fae4ccae9933ffbe9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635528"
---
# <a name="linq-to-xml-axes-overview-c"></a>LINQ - XML Eksenlerine Genel Bakış (C#)
Bir XML ağacı oluşturduktan veya bir XML ağacına bir XML belgesi yükledikten sonra, öğeleri ve öznitelikleri bulmak ve değerlerini almak için belgeyi sorgulayabilirsiniz. Eksen *yöntemleri*ile koleksiyonları almak , ayrıca *eksenler*denir. Eksenlerden bazıları koleksiyonları <xref:System.Xml.Linq.XElement> döndüren <xref:System.Xml.Linq.XDocument> <xref:System.Collections.Generic.IEnumerable%601> ve sınıflarda kullanılan yöntemlerdir. Eksenlerden bazıları sınıftaki <xref:System.Xml.Linq.Extensions> uzantı yöntemleridir. Uzantı yöntemi olarak uygulanan eksenler koleksiyonlar üzerinde çalışır ve koleksiyonları döndürer.  
  
 [XElement Sınıf Genel Bakış'ta](./xelement-class-overview.md)açıklandığı gibi, bir <xref:System.Xml.Linq.XElement> nesne tek bir öğe düğümtemsil eder. Bir öğenin içeriği karmaşık (bazen yapılandırılmış içerik olarak adlandırılır) veya basit bir öğe olabilir. Basit bir öğe boş olabilir veya bir değer içerebilir. Düğüm yapılandırılmış içerik içeriyorsa, soyundan gelen öğelerin sayısalasyonlarını almak için çeşitli eksen yöntemlerini kullanabilirsiniz. En sık kullanılan eksen <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemleri <xref:System.Xml.Linq.XContainer.Descendants%2A>ve .  
  
 Koleksiyonları döndüren eksen yöntemlerine ek olarak, sorgularda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yaygın olarak kullanacağınız iki yöntem daha vardır. Yöntem <xref:System.Xml.Linq.XContainer.Element%2A> tek <xref:System.Xml.Linq.XElement>bir . Yöntem <xref:System.Xml.Linq.XElement.Attribute%2A> tek <xref:System.Xml.Linq.XAttribute>bir .  
  
 Birçok amaç için, LINQ sorguları bir ağacı incelemek, ondan veri ayıklamak ve dönüştürmek için en güçlü yolu sağlar. <xref:System.Collections.Generic.IEnumerable%601>LINQ sorguları uygulayan nesnelerde, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> koleksiyonların eksenler ve <xref:System.Collections.Generic.IEnumerable%601> koleksiyonların <xref:System.Xml.Linq.XAttribute> iadesi üzerinde çalışır. Sorgularınızı gerçekleştirmek için bu koleksiyonlara ihtiyacınız vardır.  
  
 Öğelerin ve özniteliklerin koleksiyonlarını alan eksen yöntemlerine ek olarak, ağaç ta ayrıntılı olarak yinelemenizi sağlayan eksen yöntemleri de vardır. Örneğin, öğeler ve özniteliklerle uğraşmak yerine, ağacın düğümleriyle çalışabilirsiniz. Düğümler, öğelerden ve özniteliklerden daha ince bir tanecik düzeyidir. Düğümlerle çalışırken XML yorumlarını, metin düğümlerini, işleme yönergelerini ve daha fazlasını inceleyebilirsiniz. Bu işlev, örneğin, sözcük işlemcisi yazan ve belgeleri XML olarak kaydetmek isteyen biri için önemlidir. Ancak, XML programcıların çoğunluğu öncelikle öğeler, öznitelikler ve değerleri ile ilgilidir.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Elementler Koleksiyonunu Alma Yöntemleri  
 Aşağıda, bir öğe koleksiyonunu döndürmek <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XElement> için çağrıda aldığınız sınıfın (veya temel sınıflarının) yöntemlerinin bir özeti verilmiştir.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Bu <xref:System.Collections.Generic.IEnumerable%601> elementin atalarından <xref:System.Xml.Linq.XElement> birini döndürür. Aşırı yük, <xref:System.Collections.Generic.IEnumerable%601> belirtilene sahip atalardan birini <xref:System.Xml.Linq.XElement> döndürür. <xref:System.Xml.Linq.XName>|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Bu <xref:System.Collections.Generic.IEnumerable%601> öğenin <xref:System.Xml.Linq.XElement> torunlarından birini döndürür. Aşırı yük, <xref:System.Collections.Generic.IEnumerable%601> belirtilene sahip torunların birini <xref:System.Xml.Linq.XElement> döndürür. <xref:System.Xml.Linq.XName>|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Bu <xref:System.Collections.Generic.IEnumerable%601> öğenin <xref:System.Xml.Linq.XElement> alt öğelerinden birini döndürür. Aşırı yük, <xref:System.Collections.Generic.IEnumerable%601> belirtilen <xref:System.Xml.Linq.XElement> alt öğelerden birini <xref:System.Xml.Linq.XName>döndürür.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Bu <xref:System.Collections.Generic.IEnumerable%601> öğeden sonra gelen öğelerden birini <xref:System.Xml.Linq.XElement> döndürür. Aşırı yük, <xref:System.Collections.Generic.IEnumerable%601> belirtilen <xref:System.Xml.Linq.XElement> öğeye sahip olan bu <xref:System.Xml.Linq.XName>öğeden sonra öğelerin birini döndürür.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Bu <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> öğeden önce gelen öğelerden birini döndürür. Aşırı yük, <xref:System.Collections.Generic.IEnumerable%601> belirtilen <xref:System.Xml.Linq.XElement> öğeyi oluşturan bu öğeden <xref:System.Xml.Linq.XName>önce öğelerin birini döndürür.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Bu <xref:System.Collections.Generic.IEnumerable%601> elementin bir kısmını <xref:System.Xml.Linq.XElement> ve atalarını döndürür. Aşırı yük, <xref:System.Collections.Generic.IEnumerable%601> belirtilen <xref:System.Xml.Linq.XElement> öğelerin birini <xref:System.Xml.Linq.XName>döndürür.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Bu <xref:System.Collections.Generic.IEnumerable%601> öğenin <xref:System.Xml.Linq.XElement> bir ve onun soyundan döner. Aşırı yük, <xref:System.Collections.Generic.IEnumerable%601> belirtilen <xref:System.Xml.Linq.XElement> öğelerin birini <xref:System.Xml.Linq.XName>döndürür.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Tek Bir Öğeyi Alma Yöntemi  
 Aşağıdaki yöntem, bir <xref:System.Xml.Linq.XElement> nesneden tek bir alt alır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Belirtilen ilk <xref:System.Xml.Linq.XElement> alt nesneyi <xref:System.Xml.Linq.XName>döndürür.|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Öznitelik Koleksiyonu Alma Yöntemi  
 Aşağıdaki yöntem bir <xref:System.Xml.Linq.XElement> nesneözden öznitelikleri alır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Tüm <xref:System.Collections.Generic.IEnumerable%601> özniteliklerden birini <xref:System.Xml.Linq.XAttribute> döndürür.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Tek Bir Öznitelik Alma Yöntemi  
 Aşağıdaki yöntem bir <xref:System.Xml.Linq.XElement> nesneden tek bir öznitelik alır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Belirtilenleri <xref:System.Xml.Linq.XAttribute> döndürür. <xref:System.Xml.Linq.XName>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Eksenleri (C#)](linq-to-xml-axes-overview.md)
