---
title: XML Şema Nesne Modeline (SOM) Genel Bakış
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
ms.openlocfilehash: 3ebf0cd06ebea3092ef8aa42debe0afeac9be4f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129141"
---
# <a name="xml-schema-object-model-overview"></a>XML Şema Nesne Modeline (SOM) Genel Bakış
Microsoft .NET çerçevesindeki şema nesne modeli (SOM), şemaları programlı bir şekilde oluşturmanıza, düzenlemenize ve doğrulamanıza olanak sağlayan zengin bir API 'dir. SOM, XML şeması belgelerinde Belge Nesne Modeli (DOM) XML belgelerinde çalışma biçimine benzer şekilde çalışır. XML şeması belgeleri, SOM 'a bir kez yüklendikten sonra şemaya uygun diğer XML belgelerinin yapısı ve geçerliliği hakkında anlam veren geçerli XML dosyalarıdır.  
  
 Şema, belirli bir şema için XML belgelerinin yapısını veya modelini belirterek XML belgelerinin bir sınıfını tanımlayan bir XML belgesidir. Bir şema, XML belgelerinin içeriğiyle ilgili kısıtlamaları tanımlar ve uyumlu XML belgelerinin, şema için geçerli olan şemayla birlikte kabul edilebilmesi için izlenmesi gereken sözlük (kurallar veya dilbilgisi) açıklanmaktadır. Bir XML belgesinin doğrulanması, belgenin şema tarafından belirtilen dilbilgisine uyduğundan emin olmanızı sağlayan işlemdir.  
  
 Aşağıda, .NET Framework 'teki SOM API 'sinin şemaları oluşturmanıza, düzenlemenize ve doğrulamanıza olanak tanıyan yollar verilmiştir.  
  
- Dosyalardan ve dosyalarından geçerli şemaları yükleyin ve kaydedin.  
  
- Kesin olarak belirlenmiş sınıfları kullanarak bellek içi şemalar oluşturun.  
  
- Şemaları önbelleğe alma <xref:System.Xml.Schema.XmlSchemaSet> , derleme ve alma amacıyla sınıfla etkileşime geçin.  
  
- XML örnek belgelerinin <xref:System.Xml.XmlReader.Create%2A> şemalara karşı doğrulanması <xref:System.Xml.XmlReader> için sınıfının yöntemiyle etkileşime geçin.  
  
- Şemaları oluşturmaya ve korumaya yönelik düzenleyiciler oluşturun.  
  
- Karmaşık ve XML örnek belgelerinin doğrulamasında kullanılmak üzere kaydedilebilecek bir şemayı dinamik olarak düzenleyin.  
  
## <a name="the-schema-object-model"></a>Şema nesne modeli  
 SOM, bir XML şemasındaki öğelere karşılık gelen <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanındaki kapsamlı bir sınıf kümesinden oluşur. Örneğin, `<xsd:schema>...</xsd:schema>` öğesi <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> sınıfıyla eşlenir ve bir `<xsd:schema/>` öğe içinde yer alan tüm bilgiler <xref:System.Xml.Schema.XmlSchema> sınıfı kullanılarak temsil edilebilir. Benzer şekilde, `<xsd:element>...</xsd:element>` ve `<xsd:attribute>...</xsd:attribute>` öğeleri sırasıyla <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> ve <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> sınıflarıyla eşlenir. Bu eşleme, izleyen diyagramda gösterilen <xref:System.Xml.Schema> ad alanında bir XML şeması nesne modeli oluşturan bir XML şemasının tüm öğeleri için devam eder.  
  
 ![System. xml. Schema nesne modeli](./media/xml-schema-object-model-overview/xml-schema-object-model.gif)  
  
 <xref:System.Xml.Schema> Ad alanındaki her sınıf hakkında daha fazla bilgi için, .NET Framework sınıf <xref:System.Xml.Schema> kitaplığındaki ad alanı başvurusu belgelerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [XML Şemalarını Çapraz Geçirme](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
