---
title: LINQ to XML eksenlerine genelC#bakış ()
ms.date: 07/20/2015
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
ms.openlocfilehash: b775a37869f0c8baa7d482475e301347cb77c538
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591929"
---
# <a name="linq-to-xml-axes-overview-c"></a>LINQ to XML eksenlerine genelC#bakış ()
Bir xml ağacını oluşturduktan veya bir XML ağacına bir XML belgesi yükledikten sonra, öğeleri ve öznitelikleri bulmak ve değerlerini almak için onu sorgulayabilirsiniz. Koleksiyonları, eksen olarak da adlandırılan *eksen yöntemleri*aracılığıyla alırsınız. Eksenlerden bazıları, <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> koleksiyonları döndüren <xref:System.Collections.Generic.IEnumerable%601> sınıflarda yer alan yöntemlerdir. Eksenlerden bazıları, <xref:System.Xml.Linq.Extensions> sınıfındaki genişletme yöntemleridir. Uzantı yöntemleri olarak uygulanan eksenler koleksiyonlar üzerinde çalışır ve koleksiyonlar döndürülür.  
  
 [XElement sınıfına genel bakış](./xelement-class-overview.md)bölümünde açıklandığı gibi, <xref:System.Xml.Linq.XElement> bir nesne tek bir öğe düğümünü temsil eder. Bir öğenin içeriği karmaşık olabilir (bazen yapılandırılmış içerik olarak adlandırılır) veya basit bir öğe olabilir. Basit bir öğe boş olabilir veya bir değer içerebilir. Düğüm yapısal içerik içeriyorsa, alt öğelerin numaralandırmalar almak için çeşitli eksen yöntemlerini kullanabilirsiniz. En yaygın kullanılan eksen yöntemleri ve ' <xref:System.Xml.Linq.XContainer.Elements%2A> <xref:System.Xml.Linq.XContainer.Descendants%2A>dir.  
  
 Koleksiyonları döndüren eksen yöntemlerine ek olarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgularda yaygın olarak kullanabileceğiniz iki yöntem vardır. <xref:System.Xml.Linq.XContainer.Element%2A> Yöntemi tek<xref:System.Xml.Linq.XElement>bir döndürür. <xref:System.Xml.Linq.XElement.Attribute%2A> Yöntemi tek<xref:System.Xml.Linq.XAttribute>bir döndürür.  
  
 Birçok amaç [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] için sorgular, bir ağacı incelemek, verileri dosyadan ayıklamak ve dönüştürmek için en güçlü yolu sağlar. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<xref:System.Collections.Generic.IEnumerable%601>sorgular, uygulayan nesneler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve koleksiyonlar <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> ve <xref:System.Collections.Generic.IEnumerable%601> koleksiyonlar döndüren nesneler üzerindeçalışır.<xref:System.Xml.Linq.XAttribute> Sorgularınızı gerçekleştirmek için bu koleksiyonlara ihtiyacınız vardır.  
  
 Öğe ve özniteliklerin koleksiyonlarını alan eksen yöntemlerine ek olarak, ağaç üzerinde harika ayrıntılarla yineleme yapmanızı sağlayan eksen yöntemleri vardır. Örneğin, öğeleri ve öznitelikleri kullanmak yerine, ağacın düğümleri ile çalışabilirsiniz. Düğümler, öğe ve özniteliklerin daha ayrıntılı bir düzeyde ayrıntı düzeyidir. Düğümlerle çalışırken, XML açıklamalarını, metin düğümlerini, işleme talimatlarını ve daha fazlasını inceleyebilirsiniz. Bu işlevsellik, örneğin, bir sözcük işlemcisi yazan ve belgeleri XML olarak kaydetmek isteyen bir kişiye önemlidir. Ancak, XML programcılarının çoğunluğu öncelikle öğeler, öznitelikler ve değerleri ile ilgilidir.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Öğe koleksiyonunu alma yöntemleri  
 Aşağıda bir öğe koleksiyonu döndürmek <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XElement> için üzerinde çağırdığınız sınıfının (veya temel sınıflarının) yöntemlerinin bir özeti verilmiştir.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Bu öğenin üst <xref:System.Xml.Linq.XElement> öğelerinden birinidöndürür.<xref:System.Collections.Generic.IEnumerable%601> Aşırı yükleme, belirtilen <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XName>üst <xref:System.Xml.Linq.XElement> öğelerinden birini döndürür.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Bu öğenin alt <xref:System.Xml.Linq.XElement> öğelerinin birinidöndürür.<xref:System.Collections.Generic.IEnumerable%601> Aşırı yükleme, belirtilen <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XName>alt <xref:System.Xml.Linq.XElement> öğelerin birini döndürür.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Bu öğenin alt <xref:System.Xml.Linq.XElement> öğelerinden birinidöndürür.<xref:System.Collections.Generic.IEnumerable%601> Aşırı yükleme, belirtilen <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XName>alt <xref:System.Xml.Linq.XElement> öğelerinden birini döndürür.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Bu öğeden sonra <xref:System.Xml.Linq.XElement> gelen öğelerin birinidöndürür.<xref:System.Collections.Generic.IEnumerable%601> Aşırı yükleme, belirtilen <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XName>bu <xref:System.Xml.Linq.XElement> öğeden sonraki öğelerinden birini döndürür.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Bu öğeden önce <xref:System.Xml.Linq.XElement> gelen öğelerin birinidöndürür.<xref:System.Collections.Generic.IEnumerable%601> Aşırı yükleme, belirtilen <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XName>bu <xref:System.Xml.Linq.XElement> öğeden önceki öğelerinden birini döndürür.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Bu öğenin ve <xref:System.Xml.Linq.XElement> onun üst öğelerinden birinidöndürür.<xref:System.Collections.Generic.IEnumerable%601> Aşırı yükleme, belirtilen <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XName>öğelerinden <xref:System.Xml.Linq.XElement> birini döndürür.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Bu öğenin ve <xref:System.Xml.Linq.XElement> alt öğelerinin birinidöndürür.<xref:System.Collections.Generic.IEnumerable%601> Aşırı yükleme, belirtilen <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XName>öğelerinden <xref:System.Xml.Linq.XElement> birini döndürür.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Tek bir öğe alma yöntemi  
 Aşağıdaki yöntem bir <xref:System.Xml.Linq.XElement> nesneden tek bir alt öğe alır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|<xref:System.Xml.Linq.XElement> Belirtilen<xref:System.Xml.Linq.XName>ilk alt nesneyi döndürür.|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Özniteliklerin koleksiyonunu alma yöntemi  
 Aşağıdaki yöntem bir <xref:System.Xml.Linq.XElement> nesnesinden öznitelikleri alır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Tüm özniteliklerin <xref:System.Xml.Linq.XAttribute>birinidöndürür. <xref:System.Collections.Generic.IEnumerable%601>|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Tek bir özniteliği alma yöntemi  
 Aşağıdaki yöntem bir <xref:System.Xml.Linq.XElement> nesnesinden tek bir özniteliği alır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|<xref:System.Xml.Linq.XAttribute> Belirtilen<xref:System.Xml.Linq.XName>' i döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (C#)](./linq-to-xml-axes.md)
