---
title: XML ve SOAP seri hale getirme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d5b89392801e7cf85fcda121a86d0bda4e7ac18
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="xml-and-soap-serialization"></a>XML ve SOAP seri hale getirme
XML serileştirme dönüştürür (serileştiren) genel alanlar ve bir nesne veya özelliklerini parametreler ve dönüş değerleri için belirli bir XML Şeması Tanım Dili (XSD) belge uyan bir XML akışı içine yöntemlerin. XML serileştirme kesin türü belirtilmiş sınıfları genel özellikleri ve bir seri biçiminde (Bu durumda, XML) depolama veya taşıma için dönüştürülür alanları ile sonuçlanır.  
  
 XML açık bir standart olduğundan, XML akışı gerektiğinde platformundan bağımsız olarak herhangi bir uygulama tarafından işlenebilir. XML Web Hizmetleri gibi ASP.NET kullanım kullanılarak oluşturulan <xref:System.Xml.Serialization.XmlSerializer> internet veya intranet üzerinde XML Web hizmeti uygulamalar arasında veri iletmek XML akışlar oluşturmak üzere sınıfı. Buna karşılık, seri durumdan çıkarma gibi bir XML akışı alır ve nesneyi yeniden oluşturur.  
  
 XML serileştirme, SOAP belirtimine uygun XML akışları içine nesneleri seri hale getirmek için de kullanılabilir. SOAP, özellikle XML kullanarak yordam çağrıları taşımak için tasarlanmış XML, tabanlı bir protokoldür.  
  
 Serileştirmek veya seri durumdan nesneleri için kullanmak <xref:System.Xml.Serialization.XmlSerializer> sınıfı. Serileştirilecek sınıflar oluşturmak için XML şema tanımı aracını kullanın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Giriş XML serileştirme](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 Genel bir tanımı serileştirme, özellikle XML serileştirme için sağlar.  
  
 [Nasıl yapılır: bir nesneyi serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 Nesneyi serileştirmek için adım adım yönergeler sağlar.  
  
 [Nasıl yapılır: bir nesne seri durumdan](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 Bir nesne seri durumdan çıkarmak için adım adım yönergeler sağlar.  
  
 [XML serileştirme örnekleri](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 XML serileştirme temelleri gösteren örnekleri sağlar.  
  
 [XML şema tanımı aracı ve XML serileştirme](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 XML şema tanımı araç, belirli bir XML şeması tanım dili (XSD) şeması uyması sınıflar oluşturmak için veya bir .dll dosyasından bir XML şeması oluşturmak için nasıl kullanılacağını açıklar.  
  
 [XML serileştirme özniteliklerini kullanarak denetleme](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 Serileştirme özniteliklerini kullanarak denetlemek açıklar.  
  
 [XML serileştirme denetim öznitelikleri](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 XML serileştirme denetlemek için kullanılan öznitelikleri listeler.  
  
 [Nasıl yapılır: bir XML akışı için bir diğer öğe adı belirtin](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 Seri hale getirme geçersiz kılarak birden çok XML akışı oluşturmak nasıl gösteren Gelişmiş bir senaryo gösterir.  
  
 [Nasıl yapılır: denetim türetilen sınıfların serileştirme](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 Türetilen sınıflar serileştirmek denetlemek nasıl bir örnek sağlar.  
  
 [Nasıl yapılır: XML öğesi ve XML öznitelik adları nitelemek](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 Tanımlamak ve XML akışında kullanılan hangi XML ad alanları şeklini denetlemek açıklar.  
  
 [XML Web Hizmetleri ile XML serileştirme](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 XML serileştirme XML Web hizmetleri nasıl kullanıldığı açıklanmaktadır.  
  
 [Nasıl yapılır: bir SOAP kodlanmış XML akışı olarak bir nesneyi serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 Nasıl kullanılacağını açıklar <xref:System.Xml.Serialization.XmlSerializer> "Basit Nesne Erişim Protokolü (SOAP) 1.1." başlıklı bölüme World Wide Web Konsorsiyumu (www.w3.org) belgenin 5 uygun kodlanmış SOAP XML akışlar oluşturmak üzere sınıfı  
  
 [Nasıl yapılır: Kodlanmış SOAP XML serileştirmesi için geçersiz kılma](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 Nesneleri serileştirmek XML SOAP iletilerini olarak geçersiz kılma işlemini açıklar.  
  
 [Kodlanmış SOAP serileştirme denetim öznitelikleri](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 SOAP kodlanmış serileştirme denetlemek için kullanılan öznitelikleri listeler.  
  
 [\<dizileştirme mekanizmasını System.xml.Serialization > öğesi](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 XML serileştirme denetlemek için üst düzey yapılandırma öğesi.  
  
 [\<dateTimeSerialization > öğesi](../../../docs/standard/serialization/datetimeserialization-element.md)  
 Seri hale getirme modunu denetimleri <xref:System.DateTime> nesneleri.  
  
 [\<schemaImporterExtensions > öğesi](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfı.  
  
 [\<Ekle > öğesi için \<xmlSchemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 Tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Gelişmiş geliştirme teknolojileri](http://msdn.microsoft.com/en-us/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 Gelişmiş geliştirme görevlerini ve .NET Framework teknikleri hakkında daha fazla bilgi için bağlantılar sağlar.  
  
 [ASP.NET ve XML Web hizmeti istemcileri kullanılarak oluşturulan XML Web Hizmetleri](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 Açıklayan ve ASP.NET kullanarak XML Web Hizmetleri program açıklayan konuları sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İkili seri hale getirme](../../../docs/standard/serialization/binary-serialization.md)
