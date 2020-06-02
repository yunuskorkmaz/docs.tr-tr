---
title: XML Tür Desteği Uygulama Notları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
ms.openlocfilehash: 91a685f122ff846217ea7a8677b29df430b65363
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290285"
---
# <a name="xml-type-support-implementation-notes"></a>XML Tür Desteği Uygulama Notları
Bu konuda, farkında olmak istediğiniz bazı uygulama ayrıntıları açıklanmaktadır.  
  
## <a name="list-mappings"></a>Eşlemeleri Listele  
 <xref:System.Collections.IList>,, <xref:System.Collections.ICollection> , <xref:System.Collections.IEnumerable> **Türü []** ve <xref:System.String> türleri XML şeması tanım dili (xsd) liste türlerini temsil etmek için kullanılır.  
  
## <a name="union-mappings"></a>Birleşim eşlemeleri  
 Birleşim türleri veya türü kullanılarak temsil <xref:System.Xml.Schema.XmlAtomicValue> edilir <xref:System.String> . Bu nedenle, kaynak türü veya hedef türü her zaman ya da <xref:System.String> olmalıdır <xref:System.Xml.Schema.XmlAtomicValue> .  
  
 <xref:System.Xml.Schema.XmlSchemaDatatype>Nesne bir liste türünü temsil ediyorsa, nesne giriş dize değerini bir veya daha fazla nesne listesine dönüştürür. Eğer <xref:System.Xml.Schema.XmlSchemaDatatype> bir birleşim türünü temsil ediyorsa, giriş değerini birleşimin üye türü olarak ayrıştırmaya yönelik bir girişim yapılır. Ayrıştırma denemesi başarısız olursa, dönüştürme işleminin bir sonraki üyesi ile denenir ve dönüştürme başarılı olana kadar ya da denenecek başka hiçbir üye türü yoksa, bu durumda bir özel durum oluşturulur.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>CLR ve XML veri türleri arasındaki farklar  
 Aşağıda, CLR türleri ve XML veri türleri arasında oluşabilecek bazı uyuşmazlıklar ve bunların nasıl işlendiği açıklanmaktadır.  
  
> [!NOTE]
> `xs`Ön ek <https://www.w3.org/2001/XMLSchema> ve ad alanı URI 'sine eşlenir.
  
### <a name="systemtimespan-and-xsduration"></a>System. TimeSpan ve xs: Duration  
 `xs:duration`Tür, farklı ancak eşdeğer olan belirli Duration değerleri olacak şekilde kısmen sıralanır. Bu, `xs:duration` 1 ay (P1M) gibi tür değeri için 32 günden (p32d), 27 günden (P27D) daha büyük ve 28, 29 veya 30 güne eşit olduğu anlamına gelir.  
  
 <xref:System.TimeSpan>Sınıfı bu kısmi sıralamayı desteklemiyor. Bunun yerine, 1 yıl ve 1 ay için belirli sayıda gün seçer; 365 gün ve 30 gün sırasıyla.  
  
 Tür hakkında daha fazla bilgi için `xs:duration` bkz. W3C [XML şeması Bölüm 2: veri türleri önerisi](https://www.w3.org/TR/xmlschema-2/).
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>xs: Time, Gregoryen tarih türleri ve System. DateTime  
 Bir `xs:time` değer bir <xref:System.DateTime> nesneyle eşlendiğinde, <xref:System.DateTime.MinValue> nesnenin tarih özelliklerini <xref:System.DateTime> (örneğin <xref:System.DateTime.Year%2A> , <xref:System.DateTime.Month%2A> ve <xref:System.DateTime.Day%2A> ) en küçük olası <xref:System.DateTime> değere başlatmak için alanı kullanılır.  
  
 Benzer şekilde,, `xs:gMonth` , `xs:gDay` `xs:gYear` ve örnekleri `xs:gYearMonth` `xs:gMonthDay` de bir <xref:System.DateTime> nesneye eşlenir. Nesnedeki kullanılmayan özellikler, <xref:System.DateTime> öğesinden bu bilgisayarlara başlatılır <xref:System.DateTime.MinValue> .  
  
> [!NOTE]
> <xref:System.DateTime.Year%2A?displayProperty=nameWithType>İçerik olarak yazıldığında değere güvenebilirsiniz `xs:gMonthDay` . <xref:System.DateTime.Year%2A?displayProperty=nameWithType>Bu durumda değer her zaman 1904 olarak ayarlanır.  
  
### <a name="xsanyuri-and-systemuri"></a>xs: anyURI ve System. Uri  
 `xs:anyURI`Göreli BIR URI 'yi temsil eden öğesinin bir örneği bir ile eşlendiğinde <xref:System.Uri> , <xref:System.Uri> nesnenin temel URI 'si yoktur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [System.Xml Sınıflarında Tür Desteği](type-support-in-the-system-xml-classes.md)
