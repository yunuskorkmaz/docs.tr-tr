---
title: DOM’da XML Belgesi Doğrulama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b25bf81a17b14da558fb002b4740e31d6cda7a82
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040446"
---
# <a name="validating-an-xml-document-in-the-dom"></a>DOM’da XML Belgesi Doğrulama

<xref:System.Xml.XmlDocument> Sınıfı, varsayılan olarak bir XML şeması tanım dili (xsd) şemasına veya belge türü tanımına (DTD) göre belge nesne modeli (DOM) XML 'sini doğrulamaz; XML yalnızca iyi biçimlendirilmiş olarak doğrulanır.

Dom 'daki XML 'i doğrulamak için, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlDocument> sınıfın <xref:System.Xml.XmlDocument.Load%2A> yöntemine bir şema doğrulaması geçirerek XML 'yi doğrulayabilir veya şunu kullanarak Dom'daöncedendoğrulanmamışbirXMLbelgesinidoğrulayabilirsiniz.sınıfının<xref:System.Xml.XmlDocument.Validate%2A>yöntemi. <xref:System.Xml.XmlDocument>

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>DOM 'a yüklenen bir XML belgesini doğrulama

Sınıfı, sınıfının<xref:System.Xml.XmlDocument> yöntemine bir doğrulama <xref:System.Xml.XmlReader> <xref:System.Xml.XmlDocument.Load%2A> geçirildiğinde Dom 'a yüklendiğinde XML verilerini doğrular. <xref:System.Xml.XmlDocument>

Başarılı doğrulamadan sonra, şema Varsayılanları uygulandıktan sonra, metin değerleri, gereken şekilde atomik değerlere dönüştürülür ve tür bilgileri, doğrulanan bilgi öğeleriyle ilişkilendirilir. Sonuç olarak, yazılan XML verileri önceden türsüz XML verilerinin yerini alır.

### <a name="creating-an-xml-schema-validating-xmlreader"></a>XML şeması-doğrulama XmlReader oluşturma

XML şeması doğrulama <xref:System.Xml.XmlReader>oluşturmak için aşağıdaki adımları izleyin.

1. Yeni <xref:System.Xml.XmlReaderSettings> bir örnek oluşturun.

2. <xref:System.Xml.XmlReaderSettings.Schemas%2A> Örneğin özelliğine<xref:System.Xml.XmlReaderSettings> bir XML şeması ekleyin.

3. Olarak belirtin `Schema`. <xref:System.Xml.XmlReaderSettings.ValidationType%2A>

4. İsteğe bağlı <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> olarak şema <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> doğrulama hatalarını ve doğrulama sırasında karşılaşılan uyarıları işlemek için belirtin.

5. Son olarak, <xref:System.Xml.XmlReaderSettings> nesneyi <xref:System.Xml.XmlReader.Create%2A> XML belgesiyle birlikte <xref:System.Xml.XmlReader> sınıf yöntemine geçirin ve şema doğrulaması <xref:System.Xml.XmlReader>oluşturun.

### <a name="example"></a>Örnek

Aşağıdaki kod örneğinde, bir şema doğrulama <xref:System.Xml.XmlReader> , Dom 'a yüklenen XML verilerini doğrular. XML belgesinde geçersiz değişiklikler yapılmıştır ve belge yeniden doğrulandığından şema doğrulama hatalarına neden olur. Son olarak, hatalardan biri düzeltilir ve ardından XML belgesinin bir kısmı kısmen onaylanır.

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

Örnek, `contosoBooks.xml` dosyayı giriş olarak alır.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

Örnek ayrıca `contosoBooks.xsd` dosyayı giriş olarak alır.

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

DOM 'a yüklendiğinde XML verilerini doğrularken aşağıdakileri göz önünde bulundurun.

- Yukarıdaki örnekte,, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> her geçersiz bir tür ile karşılaşıldığında çağrılır. Doğrulama üzerinde ayarlanmamışsa, bir öznitelik veya öğe türü, <xref:System.Xml.Schema.XmlSchemaValidationException> doğrulama şemasında belirtilen karşılık gelen türle eşleşmezse çağrıldığında bir atılır. <xref:System.Xml.XmlDocument.Load%2A> <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> <xref:System.Xml.XmlReader>

- Bir XML belgesi, varsayılan değerleri tanımlayan ilişkili <xref:System.Xml.XmlDocument> bir şemaya sahip bir nesneye yüklendiğinde, bu varsayılan değerleri <xref:System.Xml.XmlDocument> XML belgesinde görünmiş gibi davranır. Bu, <xref:System.Xml.XmlReader.IsEmptyElement%2A> özelliğin varsayılan olarak şemadan alınan `false` bir öğe için her zaman döndürdüğü anlamına gelir. XML belgesinde bile, boş bir öğe olarak yazılmıştır.

## <a name="validating-an-xml-document-in-the-dom"></a>DOM’da XML Belgesi Doğrulama

Sınıfının yöntemi, Dom 'da yüklenen XML verilerini <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliğindeki şemalara karşı doğrular. <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> Başarılı doğrulamadan sonra, şema Varsayılanları uygulandıktan sonra, metin değerleri, gereken şekilde atomik değerlere dönüştürülür ve tür bilgileri, doğrulanan bilgi öğeleriyle ilişkilendirilir. Sonuç olarak, yazılan XML verileri önceden türsüz XML verilerinin yerini alır.

Aşağıdaki örnek, yukarıdaki "DOM 'a yüklenen bir XML belgesini doğrulama" içindeki örneğe benzerdir. Bu örnekte, XML belgesi Dom 'a yüklendiği için doğrulanmaz, ancak bunun yerine, <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemi kullanılarak Dom 'a yüklendikten sonra onaylanır. Yöntemi, XML belgesini öğesinin <xref:System.Xml.XmlDocument.Schemas%2A> <xref:System.Xml.XmlDocument>özelliğinde yer alan XML şemalarına karşı doğrular. <xref:System.Xml.XmlDocument.Validate%2A> Daha sonra XML belgesinde geçersiz değişiklikler yapılmıştır ve belge yeniden doğrulandığından şema doğrulama hatalarına neden olur. Son olarak, hatalardan biri düzeltilir ve ardından XML belgesinin bir kısmı kısmen onaylanır.

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

Örnek, `contosoBooks.xml` ve `contosoBooks.xsd` dosyalarını yukarıdaki "Dom 'a yüklendiği şekilde bir XML belgesini doğrulamak" olarak adlandırılan giriş olarak alır.

## <a name="handling-validation-errors-and-warnings"></a>Doğrulama hatalarını ve uyarılarını işleme

DOM 'da yüklenen XML verileri doğrulanırken XML şema doğrulama hataları raporlanır. XML verileri yüklenirken bulunan tüm şema doğrulama hataları veya daha önce doğrulanmamış bir XML belgesi doğrulanırken bildirim alırsınız.

Doğrulama hataları tarafından <xref:System.Xml.Schema.ValidationEventHandler>işlenir. Bir <xref:System.Xml.Schema.ValidationEventHandler> <xref:System.Xml.XmlReaderSettings> örneği, örneğe atandıysa veya <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.Validate%2A> <xref:System.Xml.Schema.XmlSchemaValidationException> yöntemine geçirilirse, şema doğrulama hatalarını işler; Aksi takdirde bir şema doğrulaması olduğunda tetiklenir <xref:System.Xml.Schema.ValidationEventHandler> hatayla karşılaşıldı.

> [!NOTE]
> XML verileri, işlemi durdurmak için bir özel durum <xref:System.Xml.Schema.ValidationEventHandler> harekete geçirmediği sürece şema doğrulama hatalarına rağmen Dom 'a yüklenir.
>
> <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> Bayrak <xref:System.Xml.XmlReaderSettings> nesneye belirtilmediği takdirde şema doğrulama uyarıları bildirilmemiştir.

 <xref:System.Xml.Schema.ValidationEventHandler>' İ gösteren örnekler için, yukarıdaki "Dom 'a yüklenen bir XML belgesini doğrulama" ve "Dom 'da bir XML belgesi doğrulama" bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [DOM Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [XML Şemalarıyla Çalışma](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
