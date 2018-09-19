---
title: Bir XML belgesi DOM doğrulanıyor
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0f5ae64eb1017570a56efab59a4bf1a66d5e02b
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006463"
---
# <a name="validating-an-xml-document-in-the-dom"></a>Bir XML belgesi DOM doğrulanıyor
<xref:System.Xml.XmlDocument> Sınıfı varsayılan olarak XML belge nesne modeli (DOM) içinde bir XML Şeması Tanım Dili (XSD) şeması veya belge türü tanımı (DTD'nin) karşı doğrulamaz; XML yalnızca doğru biçimlendirilmemiş doğrulanır.  
  
 Bu şema doğrulama geçirerek DOM'a gibi XML DOM doğrulamak için XML doğrulayabilirsiniz <xref:System.Xml.XmlReader> için <xref:System.Xml.XmlDocument.Load%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı veya kullanarakDOMdahaöncedoğrulanmamışbirXMLbelgesidoğrulama<xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.  
  
## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>DOM'da yüklü şekilde bir XML belgesi doğrulama  
 <xref:System.Xml.XmlDocument> Sınıfı doğrular XML verileri doğrularken bir DOM'da yüklü <xref:System.Xml.XmlReader> geçirilir <xref:System.Xml.XmlDocument.Load%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.  
  
 Doğrulama başarıyla tamamlandıktan sonra şema varsayılanları uygulanır, metin değerleri atomik değerleri gereken şekilde dönüştürülür ve tür bilgileri doğrulanmış bilgi öğeleri ile ilişkilidir. Sonuç olarak, daha önce türü belirsiz XML veri türü belirtilmiş XML veri değiştirir.  
  
### <a name="creating-an-xml-schema-validating-xmlreader"></a>Bir XML oluşturma XmlReader şema doğrulanıyor  
 Bir XML Şeması-doğrulama oluşturmak için <xref:System.Xml.XmlReader>, şu adımları izleyin.  
  
1.  Yeni bir oluşturmak <xref:System.Xml.XmlReaderSettings> örneği.  
  
2.  Bir XML şeması eklemek <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği <xref:System.Xml.XmlReaderSettings> örneği.  
  
3.  Belirtin `Schema` olarak <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.  
  
4.  İsteğe bağlı olarak belirtin <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> ve <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> şema doğrulama hataları ve Uyarıları doğrulama sırasında karşılaşılan işlemek için.  
  
5.  Son olarak, geçirmek <xref:System.Xml.XmlReaderSettings> nesnesini <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> şema doğrulama oluşturma, bir XML belgesi sınıfıyla <xref:System.Xml.XmlReader>.  
  
### <a name="example"></a>Örnek  
 Şema doğrulama, aşağıdaki kod örneğinde <xref:System.Xml.XmlReader> DOM'a XML verileri doğrulama Geçersiz değişiklik XML belgeye yapılan ve belgeyi daha sonra şema doğrulama hataları neden yeniden doğrulanır. Son olarak, bir hata düzeltildi ve sonra XML belgesi bir parçası kısmen doğrulanır.  
  
 [!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
 [!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]  
  
 Örnek alan `contosoBooks.xml` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Bu örnek ayrıca alır `contosoBooks.xsd` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 DOM'a yüklü XML verileri doğrularken aşağıdaki noktaları dikkate alın  
  
-   Yukarıdaki örnekte, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> geçersiz bir türe karşılaşıldığında çağrılır. Varsa bir <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> doğrulanmasını temel ayarlanmadı <xref:System.Xml.XmlReader>e <xref:System.Xml.Schema.XmlSchemaValidationException> oluşan <xref:System.Xml.XmlDocument.Load%2A> herhangi bir öznitelik veya öğenin türü doğrulama şemasında belirtilen karşılık gelen türü eşleşmiyorsa çağrılır.  
  
-   Ne zaman bir XML belgesi yüklendiği içine bir <xref:System.Xml.XmlDocument> varsayılan değerlerini tanımlayan ilişkili bir şeması ile nesne <xref:System.Xml.XmlDocument> bu varsayılan XML belgesinde göründüyse gibi davranır. Diğer bir deyişle <xref:System.Xml.XmlReader.IsEmptyElement%2A> özelliği her zaman döndürür `false` şemadan varsayılan bir öğe için. XML belgesinde boş bir öğe olarak yazılmış olsa bile.  
  
## <a name="validating-an-xml-document-in-the-dom"></a>Bir XML belgesi DOM doğrulanıyor  
 <xref:System.Xml.XmlDocument.Validate%2A> Yöntemi <xref:System.Xml.XmlDocument> sınıfı DOM şemalarda karşı yüklenen XML verileri doğrular <xref:System.Xml.XmlDocument> nesnenin <xref:System.Xml.XmlDocument.Schemas%2A> özelliği. Doğrulama başarıyla tamamlandıktan sonra şema varsayılanları uygulanır, metin değerleri atomik değerleri gereken şekilde dönüştürülür ve tür bilgileri doğrulanmış bilgi öğeleri ile ilişkilidir. Sonuç olarak, daha önce türü belirsiz XML veri türü belirtilmiş XML veri değiştirir.  
  
 Aşağıdaki örnekte, "Doğrulama bir XML belge olarak bu olan yüklenen içine DOM" örneğe benzerdir. Bu örnekte, XML belgesi doğrulanmadı DOM'da yüklenir ancak DOM'da yüklendikten sonra bunun yerine doğrulanır kullanarak <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı. <xref:System.Xml.XmlDocument.Validate%2A> Yöntemi, XML belgesi içindeki XML şemalarına göre doğrular <xref:System.Xml.XmlDocument.Schemas%2A> özelliği <xref:System.Xml.XmlDocument>. Geçersiz değişiklik sonra XML belgeye yapılan ve belgeyi daha sonra şema doğrulama hataları neden yeniden doğrulanır. Son olarak, bir hata düzeltildi ve sonra XML belgesi bir parçası kısmen doğrulanır.  
  
 [!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]  
  
 Giriş olarak örnek alır `contosoBooks.xml` ve `contosoBooks.xsd` dosyaları adlandırılan "Doğrulama bir XML belge olarak bu olduğundan yüklenen içine DOM" Yukarıdaki.  
  
## <a name="handling-validation-errors-and-warnings"></a>Doğrulama hataları ve Uyarıları işleme  
 DOM'da XML verileri doğrulamak için yüklü XML şema doğrulama hataları bildirilen XML verilerini yüklenmekte veya daha önce doğrulanmamış bir XML belgesi doğrulama sırasında doğrulanırken bulunan tüm şema doğrulama hataları hakkında bilgilendirilirsiniz.  
  
 Doğrulama hataları tarafından işlenmesini <xref:System.Xml.Schema.ValidationEventHandler>. Varsa bir <xref:System.Xml.Schema.ValidationEventHandler> atandığı <xref:System.Xml.XmlReaderSettings> örneği veya geçirilen <xref:System.Xml.XmlDocument.Validate%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama hataları işleyecek; Aksi takdirde bir <xref:System.Xml.Schema.XmlSchemaValidationException> şema doğrulaması olduğunda tetiklenir hatayla karşılaştı.  
  
> [!NOTE]
>  XML verilerinin şema doğrulama hataları rağmen DOM sürece yüklendiği, <xref:System.Xml.Schema.ValidationEventHandler> işlemini durdurmak için bir özel durum oluşturur.  
>   
>  Şema doğrulama uyarıları sürece bildirilmez <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> bayrağı belirtilen <xref:System.Xml.XmlReaderSettings> nesne.  
  
 Gösteren örnekler için <xref:System.Xml.Schema.ValidationEventHandler>, "Doğrulama bir XML belge olarak bu olduğundan yüklenen içine DOM" ve "Doğrulama bir XML belgesi, DOM" Yukarıdaki bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XmlReader>  
- <xref:System.Xml.Schema.ValidationEventHandler>  
- <xref:System.Xml.XmlReaderSettings>  
- [DOM Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
- [XML Şemalarıyla Çalışma](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
