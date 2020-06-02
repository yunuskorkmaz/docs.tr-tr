---
title: DOM’da XML Belgesi Doğrulama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
ms.openlocfilehash: 949dc52c332b17784b0e1851d178465fe4881b6f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287642"
---
# <a name="validating-an-xml-document-in-the-dom"></a>DOM’da XML Belgesi Doğrulama

<xref:System.Xml.XmlDocument>Sınıfı, varsayılan olarak BIR XML şeması tanım dili (xsd) şemasına veya belge türü tanımına (DTD) göre belge nesne modeli (DOM) XML 'sini doğrulamaz; XML yalnızca iyi biçimlendirilmiş olarak doğrulanır.

DOM 'daki XML 'i doğrulamak için, sınıfın yöntemine bir şema doğrulaması geçirerek XML 'yi doğrulayabilir <xref:System.Xml.XmlReader> <xref:System.Xml.XmlDocument.Load%2A> <xref:System.Xml.XmlDocument> veya SıNıFıN yöntemini kullanarak Dom 'da daha önce doğrulanmamış bir XML belgesini doğrulayabilirsiniz <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> .

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>DOM 'a yüklenen bir XML belgesini doğrulama

Sınıfı, <xref:System.Xml.XmlDocument> sınıfının yöntemine bir doğrulama GEÇIRILDIĞINDE Dom 'a YÜKLENDIĞINDE XML verilerini doğrular <xref:System.Xml.XmlReader> <xref:System.Xml.XmlDocument.Load%2A> <xref:System.Xml.XmlDocument> .

Başarılı doğrulamadan sonra, şema Varsayılanları uygulandıktan sonra, metin değerleri, gereken şekilde atomik değerlere dönüştürülür ve tür bilgileri, doğrulanan bilgi öğeleriyle ilişkilendirilir. Sonuç olarak, yazılan XML verileri önceden türsüz XML verilerinin yerini alır.

### <a name="creating-an-xml-schema-validating-xmlreader"></a>XML şeması-doğrulama XmlReader oluşturma

XML şeması doğrulama oluşturmak için <xref:System.Xml.XmlReader> aşağıdaki adımları izleyin.

1. Yeni bir <xref:System.Xml.XmlReaderSettings> örnek oluşturun.

2. Örneğin özelliğine bir XML şeması ekleyin <xref:System.Xml.XmlReaderSettings.Schemas%2A> <xref:System.Xml.XmlReaderSettings> .

3. `Schema`Olarak belirtin <xref:System.Xml.XmlReaderSettings.ValidationType%2A> .

4. İsteğe bağlı olarak <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> şema doğrulama hatalarını ve doğrulama sırasında karşılaşılan uyarıları işlemek için belirtin.

5. Son olarak, <xref:System.Xml.XmlReaderSettings> NESNEYI <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> XML belgesiyle birlikte sınıf yöntemine geçirin ve şema doğrulaması oluşturun <xref:System.Xml.XmlReader> .

### <a name="example"></a>Örnek

Aşağıdaki kod örneğinde, bir şema doğrulama, <xref:System.Xml.XmlReader> Dom 'a yüklenen XML verilerini doğrular. XML belgesinde geçersiz değişiklikler yapılmıştır ve belge yeniden doğrulandığından şema doğrulama hatalarına neden olur. Son olarak, hatalardan biri düzeltilir ve ardından XML belgesinin bir kısmı kısmen onaylanır.

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

Örnek, `contosoBooks.xml` dosyayı giriş olarak alır.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

Örnek ayrıca `contosoBooks.xsd` dosyayı giriş olarak alır.

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

DOM 'a yüklendiğinde XML verilerini doğrularken aşağıdakileri göz önünde bulundurun.

- Yukarıdaki örnekte,, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> her geçersiz bir tür ile karşılaşıldığında çağrılır. <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>Doğrulama üzerinde ayarlanmamışsa <xref:System.Xml.XmlReader> , bir <xref:System.Xml.Schema.XmlSchemaValidationException> <xref:System.Xml.XmlDocument.Load%2A> öznitelik veya öğe türü, doğrulama şemasında belirtilen karşılık gelen türle eşleşmezse çağrıldığında bir atılır.

- Bir XML belgesi, <xref:System.Xml.XmlDocument> varsayılan değerleri tanımlayan ilişkili bir şemaya sahip bir nesneye yüklendiğinde, bu varsayılan DEĞERLERI <xref:System.Xml.XmlDocument> XML belgesinde görünmiş gibi davranır. Bu, <xref:System.Xml.XmlReader.IsEmptyElement%2A> özelliğin `false` Varsayılan olarak şemadan alınan bir öğe için her zaman döndürdüğü anlamına gelir. XML belgesinde bile, boş bir öğe olarak yazılmıştır.

## <a name="validating-an-xml-document-in-the-dom"></a>DOM’da XML Belgesi Doğrulama

<xref:System.Xml.XmlDocument.Validate%2A>Sınıfının yöntemi, <xref:System.Xml.XmlDocument> Dom 'DA yüklenen XML verilerini nesnenin özelliğindeki şemalara karşı doğrular <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> . Başarılı doğrulamadan sonra, şema Varsayılanları uygulandıktan sonra, metin değerleri, gereken şekilde atomik değerlere dönüştürülür ve tür bilgileri, doğrulanan bilgi öğeleriyle ilişkilendirilir. Sonuç olarak, yazılan XML verileri önceden türsüz XML verilerinin yerini alır.

Aşağıdaki örnek, yukarıdaki "DOM 'a yüklenen bir XML belgesini doğrulama" içindeki örneğe benzerdir. Bu örnekte, XML belgesi DOM 'a yüklendiği için doğrulanmaz, ancak bunun yerine, sınıfının yöntemi kullanılarak DOM 'a yüklendikten sonra onaylanır <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> . <xref:System.Xml.XmlDocument.Validate%2A>Yöntemi, XML belgesini öğesinin özelliğinde yer alan XML şemalarına karşı doğrular <xref:System.Xml.XmlDocument.Schemas%2A> <xref:System.Xml.XmlDocument> . Daha sonra XML belgesinde geçersiz değişiklikler yapılmıştır ve belge yeniden doğrulandığından şema doğrulama hatalarına neden olur. Son olarak, hatalardan biri düzeltilir ve ardından XML belgesinin bir kısmı kısmen onaylanır.

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

Örnek, `contosoBooks.xml` ve `contosoBooks.xsd` dosyalarını YUKARıDAKI "Dom 'a yüklendiği şekılde bir XML belgesini doğrulamak" olarak adlandırılan giriş olarak alır.

## <a name="handling-validation-errors-and-warnings"></a>Doğrulama hatalarını ve uyarılarını işleme

DOM 'da yüklenen XML verileri doğrulanırken XML şema doğrulama hataları raporlanır. XML verileri yüklenirken bulunan tüm şema doğrulama hataları veya daha önce doğrulanmamış bir XML belgesi doğrulanırken bildirim alırsınız.

Doğrulama hataları tarafından işlenir <xref:System.Xml.Schema.ValidationEventHandler> . Bir <xref:System.Xml.Schema.ValidationEventHandler> <xref:System.Xml.XmlReaderSettings> örneği, örneğe atandıysa veya sınıfının yöntemine geçirilirse, <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama hatalarını işler; Aksi takdirde bir <xref:System.Xml.Schema.XmlSchemaValidationException> şema doğrulama hatası ile karşılaşıldığında tetiklenir.

> [!NOTE]
> XML verileri, <xref:System.Xml.Schema.ValidationEventHandler> işlemi durdurmak için bir özel durum harekete geçirmediği sürece şema doğrulama hatalarına rağmen Dom 'a yüklenir.
>
> Bayrak nesneye belirtilmediği takdirde şema doğrulama uyarıları bildirilmemiştir <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> <xref:System.Xml.XmlReaderSettings> .

 ' İ gösteren örnekler için <xref:System.Xml.Schema.ValidationEventHandler> , yukarıdaki "Dom 'A yüklenen BIR XML belgesini doğrulama" ve "Dom 'da BIR XML belgesi doğrulama" bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [DOM Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-dom-model.md)
- [XML Şemalarıyla Çalışma](working-with-xml-schemas.md)
