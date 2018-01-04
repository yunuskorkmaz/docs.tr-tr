---
title: "XML belgesi DOM içinde doğrulanıyor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 716e9baca52e9f5b7f4f24821e50b6a16aef9136
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="validating-an-xml-document-in-the-dom"></a>XML belgesi DOM içinde doğrulanıyor
<xref:System.Xml.XmlDocument> Sınıfı varsayılan olarak XML belge nesne modeli (DOM) içinde bir XML Şeması Tanım Dili (XSD) şema veya belge türü tanımı (DTD) karşı doğrulamaz; XML yalnızca iyi biçimlendirilmiş doğrulandı.  
  
 DOM şema doğrulama geçirerek yüklendi olarak DOM XML'de doğrulamak için XML doğrulayabilirsiniz <xref:System.Xml.XmlReader> için <xref:System.Xml.XmlDocument.Load%2A> yöntemi <xref:System.Xml.XmlDocument> sınıf veya kullanarakDOMöncedendoğrulanmamışbirXMLbelgesindedoğrula<xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.  
  
## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>Bir XML belgesi olarak doğrulama DOM yüklenir  
 <xref:System.Xml.XmlDocument> Sınıfı bir doğrularken DOM yüklendiği gibi XML verileri doğrular <xref:System.Xml.XmlReader> geçirilir <xref:System.Xml.XmlDocument.Load%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.  
  
 Başarılı bir doğrulama sonra şema varsayılanları uygulanır, metin değerleri gerektiği gibi atomik değerlerin dönüştürülür ve türü bilgileri doğrulanmış bilgi öğeleri ile ilişkilendirilir. Sonuç olarak, yazılı XML verilerini önceden türü belirsiz XML verileri yerini alır.  
  
### <a name="creating-an-xml-schema-validating-xmlreader"></a>Bir XML oluşturma XmlReader şema doğrulama  
 Bir XML Şeması-doğrulama oluşturmak için <xref:System.Xml.XmlReader>, şu adımları izleyin.  
  
1.  Yeni bir oluşturmak <xref:System.Xml.XmlReaderSettings> örneği.  
  
2.  Bir XML şeması eklemek <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği <xref:System.Xml.XmlReaderSettings> örneği.  
  
3.  Belirtin `Schema` olarak <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.  
  
4.  İsteğe bağlı olarak belirtin <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> ve <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> şema doğrulama hataları ve Uyarıları doğrulama sırasında karşılaşılan işlenecek.  
  
5.  Son olarak, geçirmek <xref:System.Xml.XmlReaderSettings> nesnesini <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> şema doğrulama oluşturma XML belgesi birlikte sınıfı <xref:System.Xml.XmlReader>.  
  
### <a name="example"></a>Örnek  
 Şema doğrulama, aşağıdaki kod örneğinde <xref:System.Xml.XmlReader> DOM'a XML verileri doğrulama XML belgesi geçersiz değişiklikler yapıldıktan ve belgeyi daha sonra şema doğrulama hatalarına neden yeniden doğrulanır. Son olarak, hatalardan biri düzeltilinceye ve ardından XML belgesi parçası kısmen doğrulanabilir.  
  
 [!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
 [!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]  
  
 Örnek alır `contosoBooks.xml` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Bu örnek ayrıca alır `contosoBooks.xsd` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 DOM yüklendiği gibi XML verileri doğrularken aşağıdakileri dikkate alın  
  
-   Yukarıdaki örnekte, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> geçersiz bir tür karşılaşıldığında olarak adlandırılır. Varsa bir <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> doğrulama ayarlanmadı <xref:System.Xml.XmlReader>, bir <xref:System.Xml.Schema.XmlSchemaValidationException> ne zaman oluşturulur <xref:System.Xml.XmlDocument.Load%2A> herhangi bir öznitelik veya öğe türü doğrulama şemasında belirtilen karşılık gelen türü eşleşmiyorsa olarak adlandırılır.  
  
-   Ne zaman bir XML belgesi yüklendiği içine bir <xref:System.Xml.XmlDocument> varsayılan değerleri tanımlayan bir ilişkili şema nesnesiyle <xref:System.Xml.XmlDocument> XML belgesinde göründüğü gibi bu varsayılan değerlendirir. Bunun anlamı <xref:System.Xml.XmlReader.IsEmptyElement%2A> özelliği her zaman döndürür `false` şemadan varsayılan bir öğe için. XML belgesinde boş bir öğe olarak yazılmış olsa bile.  
  
## <a name="validating-an-xml-document-in-the-dom"></a>XML belgesi DOM içinde doğrulanıyor  
 <xref:System.Xml.XmlDocument.Validate%2A> Yöntemi <xref:System.Xml.XmlDocument> sınıfı doğrular şemalarda karşı DOM yüklenmiş XML verileri <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliği. Başarılı bir doğrulama sonra şema varsayılanları uygulanır, metin değerleri gerektiği gibi atomik değerlerin dönüştürülür ve türü bilgileri doğrulanmış bilgi öğeleri ile ilişkilendirilir. Sonuç olarak, yazılı XML verilerini önceden türü belirsiz XML verileri yerini alır.  
  
 Aşağıdaki örnekte, "Doğrulama bir XML belge olarak bunu olan yüklenen içine DOM" örnekte benzerdir. DOM yüklenir, ancak DOM yüklendikten sonra yerine doğrulanır gibi bu örnekte, XML belgesi doğrulanmaz kullanarak <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı. <xref:System.Xml.XmlDocument.Validate%2A> Yöntemi XML belgesi bulunan XML şemalarına göre doğrular <xref:System.Xml.XmlDocument.Schemas%2A> özelliği <xref:System.Xml.XmlDocument>. Geçersiz değişiklikleri daha sonra XML belgesi yapılır ve belgeyi daha sonra şema doğrulama hatalarına neden yeniden doğrulanır. Son olarak, hatalardan biri düzeltilinceye ve ardından XML belgesi parçası kısmen doğrulanabilir.  
  
 [!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]  
  
 Giriş olarak örnek alır `contosoBooks.xml` ve `contosoBooks.xsd` dosyaları başvurduğu "Doğrulama bir XML belgesi olarak, olan yüklenen içine DOM'da" Yukarıdaki.  
  
## <a name="handling-validation-errors-and-warnings"></a>Doğrulama hataları ve Uyarıları işleme  
 XML verileri doğrulama DOM yüklendiğinde XML şema doğrulama hatalarıyla bildirilir XML verileri yüklenmekte gibi ya da daha önce doğrulanmamış bir XML belgesi doğrularken doğrulanırken bulunan tüm şema doğrulama hatalarıyla ilgili bildirilir.  
  
 Doğrulama hataları tarafından işlenmesini <xref:System.Xml.Schema.ValidationEventHandler>. Varsa bir <xref:System.Xml.Schema.ValidationEventHandler> atandığı <xref:System.Xml.XmlReaderSettings> örneği veya geçirilen <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı, <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama hatalarıyla işleyecek; Aksi halde bir <xref:System.Xml.Schema.XmlSchemaValidationException> şema doğrulaması tetiklenir hata ile karşılaştı.  
  
> [!NOTE]
>  XML verileri şema doğrulama hatalarıyla rağmen DOM sürece yüklenen, <xref:System.Xml.Schema.ValidationEventHandler> işlemi durdurmak için bir özel durum oluşturur.  
>   
>  Şema doğrulama uyarıları değil bildirilir sürece <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> bayrağı belirtilen <xref:System.Xml.XmlReaderSettings> nesnesi.  
  
 Gösteren örnekler için <xref:System.Xml.Schema.ValidationEventHandler>, "Doğrularken bir XML belge olarak bunu olan yüklenen içine DOM" ve "Doğrulama bir XML belgesi, DOM" Yukarıdaki bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.ValidationEventHandler>  
 <xref:System.Xml.XmlReaderSettings>  
 [DOM Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [XML Şemalarıyla Çalışma](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
