---
title: DOM’da XML Belgesi Doğrulama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
ms.openlocfilehash: 93686ddf1afff76926e77acdbf5aa58e93d6cb77
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710043"
---
# <a name="validating-an-xml-document-in-the-dom"></a>DOM’da XML Belgesi Doğrulama

<xref:System.Xml.XmlDocument> sınıfı, varsayılan olarak bir XML şeması tanım dili (XSD) şemasına veya belge türü tanımına (DTD) karşı Belge Nesne Modeli (DOM) XML 'yi doğrulamaz; XML yalnızca iyi biçimlendirilmiş olarak doğrulanır.

DOM 'daki XML 'i doğrulamak için, bir şema doğrulama <xref:System.Xml.XmlReader> <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Load%2A> yöntemine geçirerek XML 'yi doğrulayabilir veya <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemini kullanarak DOM 'da daha önce doğrulanmamış bir XML belgesini doğrulayabilirsiniz.

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>DOM 'a yüklenen bir XML belgesini doğrulama

<xref:System.Xml.XmlDocument> sınıfı, <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Load%2A> yöntemine bir doğrulama <xref:System.Xml.XmlReader> geçirildiğinde DOM 'a yüklendiğinde XML verilerini doğrular.

Başarılı doğrulamadan sonra, şema Varsayılanları uygulandıktan sonra, metin değerleri, gereken şekilde atomik değerlere dönüştürülür ve tür bilgileri, doğrulanan bilgi öğeleriyle ilişkilendirilir. Sonuç olarak, yazılan XML verileri önceden türsüz XML verilerinin yerini alır.

### <a name="creating-an-xml-schema-validating-xmlreader"></a>XML şeması-doğrulama XmlReader oluşturma

Bir XML şeması-doğrulama <xref:System.Xml.XmlReader>oluşturmak için aşağıdaki adımları izleyin.

1. Yeni bir <xref:System.Xml.XmlReaderSettings> örneği oluşturun.

2. <xref:System.Xml.XmlReaderSettings> örneğinin <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliğine bir XML şeması ekleyin.

3. <xref:System.Xml.XmlReaderSettings.ValidationType%2A>olarak `Schema` belirtin.

4. İsteğe bağlı olarak, şema doğrulama hatalarını ve doğrulama sırasında karşılaşılan uyarıları işlemek için <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> ve <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> belirtin.

5. Son olarak, <xref:System.Xml.XmlReaderSettings> nesnesini XML belgesiyle birlikte <xref:System.Xml.XmlReader> sınıfının <xref:System.Xml.XmlReader.Create%2A> yöntemine geçirin ve şema doğrulama <xref:System.Xml.XmlReader>oluşturun.

### <a name="example"></a>Örnek

Aşağıdaki kod örneğinde, bir şema doğrulama <xref:System.Xml.XmlReader> DOM 'a yüklenen XML verilerini doğrular. XML belgesinde geçersiz değişiklikler yapılmıştır ve belge yeniden doğrulandığından şema doğrulama hatalarına neden olur. Son olarak, hatalardan biri düzeltilir ve ardından XML belgesinin bir kısmı kısmen onaylanır.

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

Örnek ayrıca `contosoBooks.xsd` dosyasını girdi olarak alır.

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

DOM 'a yüklendiğinde XML verilerini doğrularken aşağıdakileri göz önünde bulundurun.

- Yukarıdaki örnekte, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> her geçersiz bir tür ile karşılaşıldığında çağrılır. Doğrulama <xref:System.Xml.XmlReader>bir <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> ayarlanmamışsa, herhangi bir öznitelik veya öğe türü, doğrulama şemasında belirtilen ilgili türle eşleşmezse <xref:System.Xml.XmlDocument.Load%2A> çağrıldığında bir <xref:System.Xml.Schema.XmlSchemaValidationException> oluşturulur.

- Bir XML belgesi, varsayılan değerleri tanımlayan ilişkili bir şemaya sahip bir <xref:System.Xml.XmlDocument> nesnesine yüklendiğinde, <xref:System.Xml.XmlDocument> bu Varsayılanları XML belgesinde görünmiş gibi davranır. Bu, <xref:System.Xml.XmlReader.IsEmptyElement%2A> özelliğinin her zaman şemadan alınan bir öğe için `false` döndürdüğü anlamına gelir. XML belgesinde bile, boş bir öğe olarak yazılmıştır.

## <a name="validating-an-xml-document-in-the-dom"></a>DOM’da XML Belgesi Doğrulama

<xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemi, DOM 'da yüklenen XML verilerini <xref:System.Xml.XmlDocument> nesnesinin <xref:System.Xml.XmlDocument.Schemas%2A> özelliğindeki şemalara karşı doğrular. Başarılı doğrulamadan sonra, şema Varsayılanları uygulandıktan sonra, metin değerleri, gereken şekilde atomik değerlere dönüştürülür ve tür bilgileri, doğrulanan bilgi öğeleriyle ilişkilendirilir. Sonuç olarak, yazılan XML verileri önceden türsüz XML verilerinin yerini alır.

Aşağıdaki örnek, yukarıdaki "DOM 'a yüklenen bir XML belgesini doğrulama" içindeki örneğe benzerdir. Bu örnekte, XML belgesi DOM 'a yüklendiği için doğrulanmaz, ancak bunun yerine <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemi kullanılarak DOM 'a yüklendikten sonra onaylanır. <xref:System.Xml.XmlDocument.Validate%2A> yöntemi, XML belgesini <xref:System.Xml.XmlDocument><xref:System.Xml.XmlDocument.Schemas%2A> özelliğindeki XML şemalarına karşı doğrular. Daha sonra XML belgesinde geçersiz değişiklikler yapılmıştır ve belge yeniden doğrulandığından şema doğrulama hatalarına neden olur. Son olarak, hatalardan biri düzeltilir ve ardından XML belgesinin bir kısmı kısmen onaylanır.

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

Örnek, yukarıdaki `contosoBooks.xml` ve `contosoBooks.xsd` dosyalarını, yukarıdaki "DOM 'a yüklendiği şekilde bir XML belgesini doğrulamak" olarak adlandırılacaktır.

## <a name="handling-validation-errors-and-warnings"></a>Doğrulama hatalarını ve uyarılarını işleme

DOM 'da yüklenen XML verileri doğrulanırken XML şema doğrulama hataları raporlanır. XML verileri yüklenirken bulunan tüm şema doğrulama hataları veya daha önce doğrulanmamış bir XML belgesi doğrulanırken bildirim alırsınız.

Doğrulama hataları <xref:System.Xml.Schema.ValidationEventHandler>tarafından işlenir. Bir <xref:System.Xml.Schema.ValidationEventHandler> <xref:System.Xml.XmlReaderSettings> örneğine atanırsa veya <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Validate%2A> yöntemine geçirildiğinde, <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama hatalarını işleymeyecektir; Aksi takdirde, bir şema doğrulama hatası ile karşılaşıldığında <xref:System.Xml.Schema.XmlSchemaValidationException> tetiklenir.

> [!NOTE]
> XML verileri, <xref:System.Xml.Schema.ValidationEventHandler> işlemi durdurmak için bir özel durum harekete geçirmediği sürece şema doğrulama hatalarına karşın DOM 'a yüklenir.
>
> <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> bayrağı <xref:System.Xml.XmlReaderSettings> nesnesine belirtilmediği takdirde şema doğrulama uyarıları raporlanır.

 <xref:System.Xml.Schema.ValidationEventHandler>gösteren örnekler için, yukarıdaki "DOM 'a yüklenen bir XML belgesini doğrulama" ve "DOM 'da XML belgesi doğrulama" bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [DOM Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [XML Şemalarıyla Çalışma](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
