---
title: "XML şemaları ile çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e21d402dce02ecb332d041f0cda651df911979ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-xml-schemas"></a>XML şemaları ile çalışma
Bir XML belgesi yanı sıra kendi öğesi ilişkileri, veri türleri ve içerik kısıtlamaları yapısını tanımlamak için bir belge türü tanımı (DTD) veya XML Şeması Tanım Dili (XSD) şeması kullanın. Bir XML belgesi World Wide Web Konsorsiyumu (W3C) Genişletilebilir İşaretleme Dili (XML) 1.0 önerisi tarafından tanımlanan tüm söz dizimi gereksinimleri karşılıyorsa doğru biçimlendirilmiş olarak kabul edilir olsa da her ikisini de olmadığı sürece, geçerli doğru biçimlendirilmiş olarak kabul edilmez ve kendi DTD ya da şema tarafından tanımlanmış kısıtlamalar için uygundur. Bu nedenle, tüm geçerli XML belgeleri doğru biçimlendirilmiş olsa da, tüm doğru biçimlendirilmiş XML belgeleri geçerli değil.  
  
 XML hakkında daha fazla bilgi için bkz: [W3C XML 1.0 öneri](http://go.microsoft.com/fwlink/?linkid=7269). XML şeması hakkında daha fazla bilgi için bkz: [W3C XML Şeması Kısım 1: yapıları öneri](http://go.microsoft.com/fwlink/?linkid=48881) ve [W3C XML Şeması Kısım 2: veri türleri öneri](http://go.microsoft.com/fwlink/?linkid=17392) öneriler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML şema nesne modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 Şema nesne modeli (SOM) içinde ele alınmıştır <xref:System.Xml.Schema?displayProperty=nameWithType> bir şema tanım dili (XSD) şeması bir dosya veya program aracılığıyla okumaya izin veren bir dizi sınıfları sağlar ad alanını bir şema bellek içi oluşturun.  
  
 [Şema derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 Anlatılmaktadır <xref:System.Xml.Schema.XmlSchemaSet> sınıfı bir önbellek burada XSD şemaları depolanabilir ve doğrulandı.  
  
 [XmlSchemaValidator gönderim tabanlı doğrulama](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 Anlatılmaktadır <xref:System.Xml.Schema.XmlSchemaValidator> gönderim tabanlı bir biçimde XSD şemaları karşı XML verileri doğrulamak için verimli, yüksek performanslı bir mekanizma sağlayan sınıf.  
  
 [Bir XML Şeması çıkarımını yapma](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 Nasıl kullanılacağı açıklanır <xref:System.Xml.Schema.XmlSchemaInference> bir XML belgesi yapısından XSD şemasını sınıfı.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XML belgesi DOM içinde doğrulanıyor](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 XML belge nesne modeli (DOM) doğrulamak nasıl ele alınmaktadır. DOM yüklenmiş olarak XML doğrulamak veya önceden doğrulanmamış bir XML belgesi DOM içinde doğrula  
  
 [XPathNavigator kullanarak şema doğrulaması](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 XML olan doğrulamak nasıl gittiğinizde ve kullanarak düzenlenebilir anlatılmaktadır <xref:System.Xml.XPath.XPathNavigator> sınıfı.
