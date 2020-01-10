---
title: XML Şemalarıyla Çalışma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
ms.openlocfilehash: 0fd7313e800024ebb7e3563cb4323c5780cbf1c3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710017"
---
# <a name="working-with-xml-schemas"></a>XML Şemalarıyla Çalışma
Bir XML belgesinin yapısını, öğe ilişkilerini, veri türlerini ve içerik kısıtlamalarını tanımlamak için bir belge türü tanımı (DTD) veya XML şema tanımlama dili (XSD) şeması kullanırsınız. Bir XML belgesi, World Wide Web Konsorsiyumu (W3C) genişletilebilir biçimlendirme dili (XML) 1,0 önerisi tarafından tanımlanan tüm sözdizimsel gereksinimleri karşılıyorsa iyi biçimlendirilmiş kabul edilse de, her ikisi de doğru biçimlendirilmemiş olmadığı müddetçe geçerli kabul edilmez DTD veya şeması tarafından tanımlanan kısıtlamalara uyar. Bu nedenle, tüm geçerli XML belgeleri iyi biçimlendirilmiş olsa da, iyi biçimlendirilmiş XML belgelerinin hepsi geçerli değildir.  
  
 XML hakkında daha fazla bilgi için bkz. [W3C XML 1,0 önerisi](https://www.w3.org/TR/REC-xml/). XML şeması hakkında daha fazla bilgi için bkz. [W3C XML şeması Bölüm 1: yapılar önerisi](https://www.w3.org/TR/xmlschema-1/) ve [W3C XML şeması Bölüm 2: veri türleri öneri](https://www.w3.org/TR/xmlschema-2/) önerileri.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 Bir dosyadaki şema tanım dili (XSD) şemasını okumanızı veya programlı olarak bir şemayı bellek içinde oluşturmasını sağlayan bir sınıf kümesi sağlayan <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanındaki şema nesne modelini (SOM) açıklar.  
  
 [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 XSD şemalarının depolanabileceği ve doğrulandığı bir önbellek olan <xref:System.Xml.Schema.XmlSchemaSet> sınıfını açıklar.  
  
 [XmlSchemaValidator Gönderim Temelli Doğrulaması](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 XML verilerini, gönderme temelli bir şekilde XSD şemalarına karşı doğrulamak için etkili ve yüksek performanslı bir mekanizma sağlayan <xref:System.Xml.Schema.XmlSchemaValidator> sınıfını açıklar.  
  
 [XML Şemasından Çıkarım Yapma](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 Bir XML belgesi yapısından bir XSD şemasını çıkarsmak için <xref:System.Xml.Schema.XmlSchemaInference> sınıfının nasıl kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DOM’da XML Belgesi Doğrulama](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 Belge Nesne Modeli (DOM) içinde XML 'nin nasıl doğrulandığını açıklar. XML 'i DOM 'a yüklendiği şekilde doğrulayabilir veya DOM 'da önceden doğrulanmamış bir XML belgesini doğrulayabilirsiniz.  
  
 [XPathNavigator Kullanarak Şema Doğrulama](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <xref:System.Xml.XPath.XPathNavigator> sınıfı kullanılarak gezinmekte olan XML 'in nasıl doğrulandığını ve düzenlendiğini açıklar.
