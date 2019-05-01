---
title: XML Şemalarıyla Çalışma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83fddd00f44b184fa066f6c47b90b01fac7ef7bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959121"
---
# <a name="working-with-xml-schemas"></a>XML Şemalarıyla Çalışma
Bir XML belgesi yanı sıra, öğe ilişkileri, veri türleri ve içerik kısıtlamaları yapısını tanımlamak için bir belge türü tanımı (DTD'nin) veya XML Şeması Tanım Dili (XSD) şemaya kullanın. Bir XML belgesi World Wide Web Consortium (W3C) Genişletilebilir Biçimlendirme Dili (XML) 1.0 önerisi tarafından tanımlanan tüm söz dizimi gereksinimlerini karşılıyorsa, doğru biçimlendirilmiş olarak değerlendirilir olsa da, her ikisi de olmadığı sürece, geçerli biçimlendirilmiş olarak kabul edilmez ve kendi DTD'nin veya şema tarafından tanımlanan kısıtlamaları uyar. Bu nedenle, tüm geçerli XML belgeleri biçimlendirildiğini olsa da, tüm doğru biçimlendirilmemiş XML belgeleri geçerlidir.  
  
 XML hakkında daha fazla bilgi için bkz: [W3C XML 1.0 öneri](https://www.w3.org/TR/REC-xml/). XML şeması hakkında daha fazla bilgi için bkz. [W3C XML Şeması Kısım 1: Yapıları öneri](https://www.w3.org/TR/xmlschema-1/) ve [W3C XML şema bölümü 2: Veri türleri öneri](https://www.w3.org/TR/xmlschema-2/) öneriler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 Şema nesne modeli (SOM) içinde ele alınmaktadır <xref:System.Xml.Schema?displayProperty=nameWithType> bir şeması tanım dili (XSD) şemaya bir dosyadaki veya program aracılığıyla okumaya izin veren bir sınıf kümesi sağlayan ad alanı, bir şema bellek içi oluşturma.  
  
 [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 Anlatılmaktadır <xref:System.Xml.Schema.XmlSchemaSet> sınıfı burada XSD şemaları depolanabilir ve doğrulanmış bir önbellek.  
  
 [XmlSchemaValidator Gönderim Temelli Doğrulaması](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 Anlatılmaktadır <xref:System.Xml.Schema.XmlSchemaValidator> gönderim temelli bir şekilde XML verileri XSD şemaları karşı doğrulamak için verimli, yüksek performanslı bir mekanizma sağlayan sınıf.  
  
 [XML Şemasından Çıkarım Yapma](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 Nasıl kullanılacağı ele alınmaktadır <xref:System.Xml.Schema.XmlSchemaInference> yapısı bir XML belgesi bir XSD şema çıkarsanacak sınıfı.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DOM’da XML Belgesi Doğrulama](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 XML belge nesne modeli (DOM) doğrulamak nasıl ele alınmaktadır. DOM'da yüklü XML'i doğrulamak veya sayısında daha önce doğrulanmamış bir XML belgesi doğrulama  
  
 [XPathNavigator Kullanarak Şema Doğrulama](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 XML doğrulamak üzere gittiğinizde ve kullanarak düzenlenebilir anlatılmaktadır <xref:System.Xml.XPath.XPathNavigator> sınıfı.
