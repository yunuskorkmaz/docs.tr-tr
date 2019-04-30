---
title: XML Tür Desteği Uygulama Notları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 73f786c8f1080d0046889958e8b3bd3165870569
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778761"
---
# <a name="xml-type-support-implementation-notes"></a>XML Tür Desteği Uygulama Notları
Bu konu, istediğiniz bazı uygulama ayrıntılarını açıklar.  
  
## <a name="list-mappings"></a>Liste eşlemeleri  
 <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Türü []**, ve <xref:System.String> türleri XML Şeması Tanım Dili (XSD) liste türleri temsil etmek için kullanılır.  
  
## <a name="union-mappings"></a>Birleşim eşlemeleri  
 Birleşim türleri kullanılarak temsil edilir <xref:System.Xml.Schema.XmlAtomicValue> veya <xref:System.String> türü. Kaynak türü veya hedef türüne bu nedenle her zaman olmalıdır <xref:System.String> veya <xref:System.Xml.Schema.XmlAtomicValue>.  
  
 Varsa <xref:System.Xml.Schema.XmlSchemaDatatype> nesnesini gösteren bir liste türü giriş dizesindeki bir veya daha fazla nesne listesi için değer nesnesi dönüştürür. Varsa <xref:System.Xml.Schema.XmlSchemaDatatype> giriş değeri bir birleşimin üyesi türü olarak ayrıştırmak için bir girişimde sonra bir birleşim türünü temsil eder. Ayrıştırma girişimi başarısız olursa sonra dönüştürme sonraki birleşim üyesi ile vb. Dönüştürme başarılı olana veya bir özel durum, bu durumda denemek için diğer bir üye türleri atılana kadar denenir.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>CLR ve XML veri türleri arasındaki farklar  
 CLR türleri ve XML veri türleri arasında nasıl işleneceğini oluşabilecek belirli eşleşmeler aşağıda açıklanmıştır.  
  
> [!NOTE]
> `xs` Önek eşlenmiş durumda <https://www.w3.org/2001/XMLSchema> ve ad alanı URI.
  
### <a name="systemtimespan-and-xsduration"></a>System.TimeSpan ve xs: Duration  
 `xs:duration` Türü, farklı belirli süre değer vardır ancak kısmen sıralandığına. İçin diğer bir deyişle `xs:duration` türü değeri 1 ay (P1M) gibi 32 günden (P32D) (P27D) 27 gün sayısından daha büyük olduğu ve 28, 29 veya 30 gün eşdeğerdir.  
  
 <xref:System.TimeSpan> Sınıfı kısmi sıralanması desteklemez. Bunun yerine, belirli sayıda gün boyunca 1 yıl ve 1 ay seçer; 365 gün ve 30 gün sırasıyla.  
  
 Daha fazla bilgi için `xs:duration` yazın, bkz: W3C [XML şema bölümü 2: Veri türleri öneri](https://www.w3.org/TR/xmlschema-2/).
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>System.DateTime xs: Time ve Gregoryen tarihi türleri  
 Olduğunda bir `xs:time` değeri eşlenmiş durumda bir <xref:System.DateTime> nesnesi <xref:System.DateTime.MinValue> tarih özelliklerini başlatmak için kullanılan alanı <xref:System.DateTime> nesne (gibi <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, ve <xref:System.DateTime.Day%2A>) en küçük olası <xref:System.DateTime> değeri.  
  
 Benzer şekilde, örneklerini `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` ve `xs:gMonthDay` de eşleştirilmiş bir <xref:System.DateTime> nesne. Kullanılmayan özellikleri <xref:System.DateTime> nesne başlatıldığı olanlardan <xref:System.DateTime.MinValue>.  
  
> [!NOTE]
>  Üzerinde güvenemezsiniz <xref:System.DateTime.Year%2A?displayProperty=nameWithType> değer olarak içerik yazıldığında `xs:gMonthDay`. <xref:System.DateTime.Year%2A?displayProperty=nameWithType> Değeri her zaman ayarı 1904 için böyle bir durumda.  
  
### <a name="xsanyuri-and-systemuri"></a>xs:anyURI ve System.Uri  
 Örneği `xs:anyURI` temsil için göreli bir URI eşlenmiş bir <xref:System.Uri>, <xref:System.Uri> nesnesinin temel URI'sini yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [System.Xml Sınıflarında Tür Desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
