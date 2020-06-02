---
title: XML Şema Nesne Modeline (SOM) Genel Bakış
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
ms.openlocfilehash: 0358efdcc2e8b86f589eea312d791610da5238db
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290337"
---
# <a name="xml-schema-object-model-overview"></a>XML Şema Nesne Modeline (SOM) Genel Bakış
Microsoft .NET çerçevesindeki şema nesne modeli (SOM), şemaları programlı bir şekilde oluşturmanıza, düzenlemenize ve doğrulamanıza olanak sağlayan zengin bir API 'dir. SOM, XML şeması belgelerinde Belge Nesne Modeli (DOM) XML belgelerinde çalışma biçimine benzer şekilde çalışır. XML şeması belgeleri, SOM 'a bir kez yüklendikten sonra şemaya uygun diğer XML belgelerinin yapısı ve geçerliliği hakkında anlam veren geçerli XML dosyalarıdır.  
  
 Şema, belirli bir şema için XML belgelerinin yapısını veya modelini belirterek XML belgelerinin bir sınıfını tanımlayan bir XML belgesidir. Bir şema, XML belgelerinin içeriğiyle ilgili kısıtlamaları tanımlar ve uyumlu XML belgelerinin, şema için geçerli olan şemayla birlikte kabul edilebilmesi için izlenmesi gereken sözlük (kurallar veya dilbilgisi) açıklanmaktadır. Bir XML belgesinin doğrulanması, belgenin şema tarafından belirtilen dilbilgisine uyduğundan emin olmanızı sağlayan işlemdir.  
  
 Aşağıda, .NET Framework 'teki SOM API 'sinin şemaları oluşturmanıza, düzenlemenize ve doğrulamanıza olanak tanıyan yollar verilmiştir.  
  
- Dosyalardan ve dosyalarından geçerli şemaları yükleyin ve kaydedin.  
  
- Kesin olarak belirlenmiş sınıfları kullanarak bellek içi şemalar oluşturun.  
  
- <xref:System.Xml.Schema.XmlSchemaSet>Şemaları önbelleğe alma, derleme ve alma amacıyla sınıfla etkileşime geçin.  
  
- <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> XML örnek belgelerinin şemalara karşı doğrulanması için sınıfının yöntemiyle etkileşime geçin.  
  
- Şemaları oluşturmaya ve korumaya yönelik düzenleyiciler oluşturun.  
  
- Karmaşık ve XML örnek belgelerinin doğrulamasında kullanılmak üzere kaydedilebilecek bir şemayı dinamik olarak düzenleyin.  
  
## <a name="the-schema-object-model"></a>Şema nesne modeli  
 SOM, <xref:System.Xml.Schema?displayProperty=nameWithType> BIR XML şemasındaki öğelere karşılık gelen ad alanındaki kapsamlı bir sınıf kümesinden oluşur. Örneğin, `<xsd:schema>...</xsd:schema>` öğesi <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> sınıfıyla eşlenir ve bir öğe içinde yer alan tüm bilgiler `<xsd:schema/>` sınıfı kullanılarak temsil edilebilir <xref:System.Xml.Schema.XmlSchema> . Benzer şekilde, `<xsd:element>...</xsd:element>` ve `<xsd:attribute>...</xsd:attribute>` öğeleri <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> sırasıyla ve sınıflarıyla eşlenir <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> . Bu eşleme, <xref:System.Xml.Schema> izleyen diyagramda gösterilen ad alanında BIR XML şeması nesne modeli oluşturan BIR XML şemasının tüm öğeleri için devam eder.  
  
 ![System. xml. Schema nesne modeli](./media/xml-schema-object-model-overview/xml-schema-object-model.gif)  
  
 Ad alanındaki her sınıf hakkında daha fazla bilgi için <xref:System.Xml.Schema> , <xref:System.Xml.Schema> .NET Framework sınıf kitaplığındaki ad alanı başvurusu belgelerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şemaları Okuma ve Yazma](reading-and-writing-xml-schemas.md)
- [XML Şemaları Derleme](building-xml-schemas.md)
- [XML Şemalarını Çapraz Geçirme](traversing-xml-schemas.md)
- [XML Şemalarını Düzenleme](editing-xml-schemas.md)
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](including-or-importing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](xmlschemaset-for-schema-compilation.md)
- [Şema Derleme Sonrası Bilgi Kümesi](post-schema-compilation-infoset.md)
