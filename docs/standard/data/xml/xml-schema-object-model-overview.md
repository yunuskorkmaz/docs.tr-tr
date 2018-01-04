---
title: "XML şema nesne modeline genel bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e18a3151228ea7edb5a8380f6ed707ee88d369e5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-schema-object-model-overview"></a>XML şema nesne modeline genel bakış
Microsoft .NET Framework şema nesne modeli (SOM) oluşturmak, düzenlemek ve şemaları program aracılığıyla doğrulayın olanak sağlayan zengin bir API'dir. SOM XML Şeması belgelerinde benzer şekilde XML belgelerini belge nesne modeli (DOM) çalıştığı şekilde çalışır. XML Şeması belgelerinde, bir kez SOM yüklenen geçerlilik XML'sini şemaya uyacak diğer XML belgelerinin ve yapısı hakkında anlam ifade geçerli XML dosyalarıdır.  
  
 Bir şema yapısı veya modeli belirli bir şema için XML belgelerinin belirterek XML belgelerinin bir sınıf tanımlayan bir XML belgesi değil. Bir şema XML belge içeriklerini kısıtlamalar tanımlar ve uyumlu XML belge şeması ile söz konusu şeması geçerli kabul edilmesi için izlemeniz gereken sözlüğünü (kuralları veya dilbilgisi) açıklar. XML belgesinin doğrulama belge şeması tarafından belirtilen dilbilgisi uymasını sağlar işlemidir.  
  
 Aşağıdaki yolları .NET Framework'teki SOM API oluşturmak, düzenlemek ve şemaları doğrulayın sağlar geçerlidir.  
  
-   Yük ve geçerli şemalar için ve dosyalarını kaydedin.  
  
-   Kesin türü belirtilmiş sınıflarını kullanarak bellek içi şemalarını oluşturun.  
  
-   Etkileşim <xref:System.Xml.Schema.XmlSchemaSet> önbelleğe derlemek ve şemaları almak için sınıf.  
  
-   Etkileşim <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> XML örneği belgeleri şemalara karşı doğrulamak için sınıf.  
  
-   Düzenleyiciler oluşturmak ve şemaları sürdürmek için oluşturun.  
  
-   Dinamik olarak derlendiğini ve XML örneği belgelerinin doğrulamada kullanmak için kaydedilen bir şema düzenleyin.  
  
## <a name="the-schema-object-model"></a>Şema nesnesi modeli  
 Sınıflarda kapsamlı bir kümesini SOM oluşan <xref:System.Xml.Schema?displayProperty=nameWithType> bir XML Şeması öğeleri karşılık gelen ad alanı. Örneğin, `<xsd:schema>...</xsd:schema>` öğesi eşler için <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> sınıfı ve içinde bulunan tüm bilgileri bir `<xsd:schema/>` öğesi kullanarak temsil edilen <xref:System.Xml.Schema.XmlSchema> sınıfı. Benzer şekilde, `<xsd:element>...</xsd:element>` ve `<xsd:attribute>...</xsd:attribute>` öğeleri eşlemek için <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> ve <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> sırasıyla sınıfları. Bu eşleme XML Şeması nesne modelinde oluşturma XML Şeması tüm öğeler için devam <xref:System.Xml.Schema> ad alanı Aşağıdaki diyagramda gösterilmiştir.  
  
 ![System.Xml.Schema nesne modeli](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")  
  
 Her sınıf hakkında daha fazla bilgi için <xref:System.Xml.Schema> ad alanı, bkz: <xref:System.Xml.Schema> .NET Framework Sınıf Kitaplığı'nda ad alanı başvuru belgeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [XML Şemalarını Çapraz Geçirme](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
