---
title: XML Şemalarıyla Çalışma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
ms.openlocfilehash: f239d67d959c1f7a0bfebfaaaa49de9cf9c9a111
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281693"
---
# <a name="working-with-xml-schemas"></a>XML Şemalarıyla Çalışma
Bir XML belgesinin yapısını, öğe ilişkilerini, veri türlerini ve içerik kısıtlamalarını tanımlamak için bir belge türü tanımı (DTD) veya XML şema tanımlama dili (XSD) şeması kullanırsınız. Bir XML belgesi, World Wide Web Konsorsiyumu (W3C) genişletilebilir biçimlendirme dili (XML) 1,0 önerisi tarafından tanımlanan tüm sözdizimsel gereksinimleri karşılıyorsa, her ikisi de doğru biçimlendirilmemiş ve DTD veya şema tarafından tanımlanan kısıtlamalara uygun olmadığı takdirde geçerli kabul edilmez. Bu nedenle, tüm geçerli XML belgeleri iyi biçimlendirilmiş olsa da, iyi biçimlendirilmiş XML belgelerinin hepsi geçerli değildir.  
  
 XML hakkında daha fazla bilgi için bkz. [W3C XML 1,0 önerisi](https://www.w3.org/TR/REC-xml/). XML şeması hakkında daha fazla bilgi için bkz. [W3C XML şeması Bölüm 1: yapılar önerisi](https://www.w3.org/TR/xmlschema-1/) ve [W3C XML şeması Bölüm 2: veri türleri öneri](https://www.w3.org/TR/xmlschema-2/) önerileri.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML Şema Nesne Modeli (SOM)](xml-schema-object-model-som.md)  
 <xref:System.Xml.Schema?displayProperty=nameWithType>Bir dosyadaki şema tanım dili (xsd) şemasını okumanızı veya programlı olarak bir şemayı bellek içinde oluşturmasını sağlayan bir sınıf kümesi sağlayan ad alanındaki şema nesne modelini (som) açıklar.  
  
 [Şema Derleme için XmlSchemaSet](xmlschemaset-for-schema-compilation.md)  
 <xref:System.Xml.Schema.XmlSchemaSet>XSD şemalarının depolanabileceği ve doğrulandığı bir önbellek olan sınıfı açıklar.  
  
 [XmlSchemaValidator Gönderim Temelli Doğrulaması](xmlschemavalidator-push-based-validation.md)  
 <xref:System.Xml.Schema.XmlSchemaValidator>XML verilerini, gönderme temelli bir şekılde xsd şemalarına karşı doğrulamak için etkili ve yüksek performanslı bir mekanizma sağlayan sınıfı açıklar.  
  
 [XML Şemasından Çıkarım Yapma](inferring-an-xml-schema.md)  
 <xref:System.Xml.Schema.XmlSchemaInference>Sınıfının BIR XML belgesi yapısından BIR xsd şemasını çıkarması için nasıl kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Xml.Schema.XmlSchemaSet>&#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124;<xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DOM’da XML Belgesi Doğrulama](validating-an-xml-document-in-the-dom.md)  
 Belge Nesne Modeli (DOM) içinde XML 'nin nasıl doğrulandığını açıklar. XML 'i DOM 'a yüklendiği şekilde doğrulayabilir veya DOM 'da önceden doğrulanmamış bir XML belgesini doğrulayabilirsiniz.  
  
 [XPathNavigator Kullanarak Şema Doğrulama](schema-validation-using-xpathnavigator.md)  
 Sınıfını kullanarak gezinmekte olan ve düzenlenmiş XML 'in nasıl doğrulandığını açıklar <xref:System.Xml.XPath.XPathNavigator> .
