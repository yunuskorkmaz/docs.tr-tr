---
title: XML şemaları ile çalışma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83fddd00f44b184fa066f6c47b90b01fac7ef7bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-xml-schemas"></a>XML şemaları ile çalışma
Bir XML belgesi yanı sıra kendi öğesi ilişkileri, veri türleri ve içerik kısıtlamaları yapısını tanımlamak için bir belge türü tanımı (DTD) veya XML Şeması Tanım Dili (XSD) şeması kullanın. Bir XML belgesi World Wide Web Konsorsiyumu (W3C) Genişletilebilir İşaretleme Dili (XML) 1.0 önerisi tarafından tanımlanan tüm söz dizimi gereksinimleri karşılıyorsa doğru biçimlendirilmiş olarak kabul edilir olsa da her ikisini de olmadığı sürece, geçerli doğru biçimlendirilmiş olarak kabul edilmez ve kendi DTD ya da şema tarafından tanımlanmış kısıtlamalar için uygundur. Bu nedenle, tüm geçerli XML belgeleri doğru biçimlendirilmiş olsa da, tüm doğru biçimlendirilmiş XML belgeleri geçerli değil.  
  
 XML hakkında daha fazla bilgi için bkz: [W3C XML 1.0 öneri](https://www.w3.org/TR/REC-xml/). XML şeması hakkında daha fazla bilgi için bkz: [W3C XML Şeması Kısım 1: yapıları öneri](https://www.w3.org/TR/xmlschema-1/) ve [W3C XML Şeması Kısım 2: veri türleri öneri](https://www.w3.org/TR/xmlschema-2/) öneriler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 Şema nesne modeli (SOM) içinde ele alınmıştır <xref:System.Xml.Schema?displayProperty=nameWithType> bir şema tanım dili (XSD) şeması bir dosya veya program aracılığıyla okumaya izin veren bir dizi sınıfları sağlar ad alanını bir şema bellek içi oluşturun.  
  
 [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 Anlatılmaktadır <xref:System.Xml.Schema.XmlSchemaSet> sınıfı bir önbellek burada XSD şemaları depolanabilir ve doğrulandı.  
  
 [XmlSchemaValidator Gönderim Temelli Doğrulaması](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 Anlatılmaktadır <xref:System.Xml.Schema.XmlSchemaValidator> gönderim tabanlı bir biçimde XSD şemaları karşı XML verileri doğrulamak için verimli, yüksek performanslı bir mekanizma sağlayan sınıf.  
  
 [XML Şemasından Çıkarım Yapma](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 Nasıl kullanılacağı açıklanır <xref:System.Xml.Schema.XmlSchemaInference> bir XML belgesi yapısından XSD şemasını sınıfı.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DOM’da XML Belgesi Doğrulama](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 XML belge nesne modeli (DOM) doğrulamak nasıl ele alınmaktadır. DOM yüklenmiş olarak XML doğrulamak veya önceden doğrulanmamış bir XML belgesi DOM içinde doğrula  
  
 [XPathNavigator Kullanarak Şema Doğrulama](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 XML olan doğrulamak nasıl gittiğinizde ve kullanarak düzenlenebilir anlatılmaktadır <xref:System.Xml.XPath.XPathNavigator> sınıfı.
