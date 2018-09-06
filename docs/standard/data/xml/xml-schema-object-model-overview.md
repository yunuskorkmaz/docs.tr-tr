---
title: XML şema nesne modeline genel bakış
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab7f3075d46ef0e8b98af471ae3943f7500128e5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037795"
---
# <a name="xml-schema-object-model-overview"></a>XML şema nesne modeline genel bakış
Microsoft .NET Framework içinde şema nesne modeli (SOM) oluşturmak, düzenlemek ve şemaları program aracılığıyla doğrulama olanak tanıyan zengin bir API'dir. SOM XML Şeması belgeleri benzer şekilde XML belgelerinde belge nesne modeli (DOM) çalıştığı şekilde çalışır. XML şema belgeleri, SOM yüklenen geçerliliğini şemaya uygun diğer XML belgeleri ve yapısı hakkında daha fazla anlam ifade geçerli XML dosyalarıdır.  
  
 Bir şema yapısı veya modeli için belirli bir şema XML belgelerinin belirterek XML belgelerinin bir sınıf tanımlayan bir XML belgesidir. Bir şema XML belgeleri içeriğini kısıtlamalar tanımlar ve uyumlu XML belgeleri şema-söz konusu şeması ile geçerli kabul edilmesi için uyması gereken sözlük (kuralları veya dilbilgisi) açıklar. Bir XML belgesi doğrulama belge şema tarafından belirtilen dil bilgisi için uygun olduğunu güvence altına işlemidir.  
  
 .NET Framework'teki SOM API yolları oluşturmak, düzenlemek ve şema doğrulama sağlayan aşağıda verilmiştir.  
  
-   Yükleyin ve geçerli şemalar dosyaları gelen ve kaydedin.  
  
-   Bellek içi şemaları kullanarak türü kesin belirlenmiş bir sınıf oluşturun.  
  
-   Etkileşim <xref:System.Xml.Schema.XmlSchemaSet> önbelleğe almak, derlemek ve şemaları almak için sınıf.  
  
-   Etkileşim <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> XML örneği belgeleri şemaları karşı doğrulamak için sınıf.  
  
-   Düzenleyiciler oluşturmak ve şemaları sürdürmek için oluşturun.  
  
-   Dinamik olarak derlendiğini ve kullanılmak üzere XML örneği belgeleri doğrulama kaydedilmiş bir şema düzenleyin.  
  
## <a name="the-schema-object-model"></a>Şema nesne modeli  
 Sınıflarda kapsamlı bir dizi SOM oluşan <xref:System.Xml.Schema?displayProperty=nameWithType> bir XML Şeması öğeleri karşılık gelen ad alanı. Örneğin, `<xsd:schema>...</xsd:schema>` öğesi eşler için <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> sınıfı ve içinde bulunan tüm bilgileri bir `<xsd:schema/>` öğesi kullanarak gösterilebileceği <xref:System.Xml.Schema.XmlSchema> sınıfı. Benzer şekilde, `<xsd:element>...</xsd:element>` ve `<xsd:attribute>...</xsd:attribute>` öğeleri eşlemek için <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> ve <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> sırasıyla sınıfları. Bu eşleme XML şeması bir XML şema nesne modeli içerisinde oluşturma tüm öğelerini Daily <xref:System.Xml.Schema> Aşağıdaki diyagramda gösterildiği ad alanı.  
  
 ![System.Xml.Schema nesne modeli](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")  
  
 Her sınıfta hakkında daha fazla bilgi için <xref:System.Xml.Schema> ad bkz <xref:System.Xml.Schema> .NET Framework sınıf kitaplığındaki ad alanı başvuru belgeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
- [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)  
- [XML Şemalarını Çapraz Geçirme](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
- [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
