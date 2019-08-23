---
title: XML Tür Desteği Uygulama Notları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 817d48e15f3a1d370e1953ca9c9aa8e10baa7f29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916029"
---
# <a name="xml-type-support-implementation-notes"></a>XML Tür Desteği Uygulama Notları
Bu konuda, farkında olmak istediğiniz bazı uygulama ayrıntıları açıklanmaktadır.  
  
## <a name="list-mappings"></a>Eşlemeleri Listele  
 <xref:System.Collections.IList> ,<xref:System.Collections.ICollection>,, **Türü []** ve<xref:System.String> türleri XML şeması tanım dili (xsd) liste türlerini temsil etmek için kullanılır. <xref:System.Collections.IEnumerable>  
  
## <a name="union-mappings"></a>Birleşim eşlemeleri  
 Birleşim türleri <xref:System.Xml.Schema.XmlAtomicValue> veya <xref:System.String> türü kullanılarak temsil edilir. Bu nedenle, kaynak türü veya hedef türü her zaman ya <xref:System.String> <xref:System.Xml.Schema.XmlAtomicValue>da olmalıdır.  
  
 <xref:System.Xml.Schema.XmlSchemaDatatype> Nesne bir liste türünü temsil ediyorsa, nesne giriş dize değerini bir veya daha fazla nesne listesine dönüştürür. Eğer bir <xref:System.Xml.Schema.XmlSchemaDatatype> birleşim türünü temsil ediyorsa, giriş değerini birleşimin üye türü olarak ayrıştırmaya yönelik bir girişim yapılır. Ayrıştırma denemesi başarısız olursa, dönüştürme işleminin bir sonraki üyesi ile denenir ve dönüştürme başarılı olana kadar ya da denenecek başka hiçbir üye türü yoksa, bu durumda bir özel durum oluşturulur.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>CLR ve XML veri türleri arasındaki farklar  
 Aşağıda, CLR türleri ve XML veri türleri arasında oluşabilecek bazı uyuşmazlıklar ve bunların nasıl işlendiği açıklanmaktadır.  
  
> [!NOTE]
> Ön ek <https://www.w3.org/2001/XMLSchema> ve ad alanı URI 'sine eşlenir. `xs`
  
### <a name="systemtimespan-and-xsduration"></a>System. TimeSpan ve xs: Duration  
 `xs:duration` Tür, farklı ancak eşdeğer olan belirli Duration değerleri olacak şekilde kısmen sıralanır. Bu, 1 ay ( `xs:duration` P1M) gibi tür değeri için 32 günden (p32d), 27 günden (P27D) daha büyük ve 28, 29 veya 30 güne eşit olduğu anlamına gelir.  
  
 <xref:System.TimeSpan> Sınıfı bu kısmi sıralamayı desteklemiyor. Bunun yerine, 1 yıl ve 1 ay için belirli sayıda gün seçer; 365 gün ve 30 gün sırasıyla.  
  
 `xs:duration` Tür hakkında daha fazla bilgi için bkz. W3C [XML şeması Bölüm 2: Veri türleri](https://www.w3.org/TR/xmlschema-2/)önerisi.
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>xs: Time, Gregoryen tarih türleri ve System. DateTime  
 <xref:System.DateTime> <xref:System.DateTime.MinValue> <xref:System.DateTime.Day%2A> <xref:System.DateTime.Month%2A>Bir değer bir nesneyle eşlendiğinde, <xref:System.DateTime> nesnenin Tarihözelliklerini(örneğin,,ve)mümkünolanenküçükdeğere(,ve)başlatmakiçinalanıkullanılır<xref:System.DateTime.Year%2A> `xs:time` <xref:System.DateTime> değer.  
  
 Benzer şekilde,, `xs:gMonth`, `xs:gDay` `xs:gYearMonth` ve `xs:gYear` örnekleride<xref:System.DateTime> bir nesneye eşlenir. `xs:gMonthDay` Nesnedeki kullanılmayan özellikler, <xref:System.DateTime> öğesinden <xref:System.DateTime.MinValue>bu bilgisayarlara başlatılır.  
  
> [!NOTE]
> İçerik olarak <xref:System.DateTime.Year%2A?displayProperty=nameWithType> `xs:gMonthDay`yazıldığında değere güvenebilirsiniz. Bu <xref:System.DateTime.Year%2A?displayProperty=nameWithType> durumda değer her zaman 1904 olarak ayarlanır.  
  
### <a name="xsanyuri-and-systemuri"></a>xs: anyURI ve System. Uri  
 Göreli bir URI 'yi `xs:anyURI` temsil eden öğesinin bir örneği bir <xref:System.Uri>ile eşlendiğinde, <xref:System.Uri> nesnenin temel URI 'si yoktur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [System.Xml Sınıflarında Tür Desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
