---
title: XML türü destek uygulama notları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4d2d6f2932e1afeb7369c32a43ca48f55fade2e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571416"
---
# <a name="xml-type-support-implementation-notes"></a>XML türü destek uygulama notları
Bu konuda farkında olmasını istediğiniz bazı uygulama ayrıntıları açıklanmaktadır.  
  
## <a name="list-mappings"></a>Liste eşlemeleri  
 <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Yazın []**, ve <xref:System.String> türleri XML Şeması Tanım Dili (XSD) liste türleri temsil etmek için kullanılır.  
  
## <a name="union-mappings"></a>Birleşim eşlemeleri  
 Birleşim türleri temsil kullanarak <xref:System.Xml.Schema.XmlAtomicValue> veya <xref:System.String> türü. Kaynak türü veya hedef türü bu nedenle her zaman ya da olmalıdır <xref:System.String> veya <xref:System.Xml.Schema.XmlAtomicValue>.  
  
 Varsa <xref:System.Xml.Schema.XmlSchemaDatatype> nesnesini temsil eden bir liste türü giriş dizesi bir veya daha fazla nesnelerin bir listesini için değer nesnesi dönüştürür. Varsa <xref:System.Xml.Schema.XmlSchemaDatatype> giriş değeri UNION bir üye türü ayrıştırmak için bir girişimde sonra bir birleşim türünü temsil eder. Ayrıştırma denemesi başarısız olursa sonra dönüştürme UNION sonraki üyesiyle vb. Dönüştürme başarılı olur veya; bu durumda bir özel durum denemek için başka bir üye türleri değiştirilene kadar denenir.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>CLR ve XML veri türleri arasındaki farklar  
 CLR türleri ve XML veri türleri arasında nasıl işleneceğini oluşabilir belirli uyuşmazlıkları açıklar.  
  
> [!NOTE]
>  `xs` Öneki eşleştirilir http://www.w3.org/2001/XMLSchema ve ad alanı URI'si.  
  
### <a name="systemtimespan-and-xsduration"></a>System.TimeSpan ve xs: Duration  
 `xs:duration` Türü kısmen sipariş edilen, farklı belirli süre değer vardır ancak eşdeğer. Bunun için anlamı `xs:duration` türü değeri 1 ay (P1M) gibi 32 günden az (P32D) (P27D) 27 gün sayısından daha büyük olduğundan ve 28, 29 veya 30 gün olarak.  
  
 <xref:System.TimeSpan> Sınıfı Bu kısmi sıralanması desteklemez. Bunun yerine, belirli bir gün için 1 yıl 1 ay sayısı seçer; 365 gün ve 30 gün sırasıyla.  
  
 Daha fazla bilgi için `xs:duration` yazın, W3C XML Şeması Kısım 2 bkz: veri türleri öneri adresindeki http://www.w3.org/TR/xmlschema-2/.  
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>xs: Time, Gregoryen tarih türleri ve System.DateTime  
 Zaman bir `xs:time` değeri eşleştirilir bir <xref:System.DateTime> nesnesi <xref:System.DateTime.MinValue> alan tarih özelliklerini başlatmak için kullanılan <xref:System.DateTime> nesne (gibi <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, ve <xref:System.DateTime.Day%2A>) en küçük olası <xref:System.DateTime> değeri.  
  
 Benzer şekilde, örneklerini `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` ve `xs:gMonthDay` için de eşlenen bir <xref:System.DateTime> nesnesi. Kullanılmayan özellikleri <xref:System.DateTime> nesne başlatılmış olanlardan için <xref:System.DateTime.MinValue>.  
  
> [!NOTE]
>  Bağlı olamaz <xref:System.DateTime.Year%2A?displayProperty=nameWithType> değeri olarak içerik yazıldığında `xs:gMonthDay`. <xref:System.DateTime.Year%2A?displayProperty=nameWithType> Değeri her zaman ayarlanır 1904 ile bu durumda.  
  
### <a name="xsanyuri-and-systemuri"></a>xs:anyURI ve System.Uri  
 Bir örneği olduğunda `xs:anyURI` temsil için göreli URI eşlenen bir <xref:System.Uri>, <xref:System.Uri> nesnesinin bir taban URI yok.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [System.Xml Sınıflarında Tür Desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
