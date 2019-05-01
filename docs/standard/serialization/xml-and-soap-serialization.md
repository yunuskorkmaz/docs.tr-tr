---
title: XML ve SOAP Serileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: d9dc68d8e7eced031af404aaec20784573c9930a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028245"
---
# <a name="xml-and-soap-serialization"></a>XML ve SOAP Serileştirme

XML serileştirme dönüştürür (serileştiren) ortak alanları ve bir nesne veya özelliklerini parametre ve dönüş değerleri yöntemlere, belirli bir XML Şeması Tanım Dili (XSD) belge uyan bir XML akışı. XML serileştirme ortak özellikler ve bir seri biçiminde (Bu durumda, XML) depolama veya taşıma için dönüştürülür alanları kesin türü belirtilmiş sınıflarıyla sonuçlanır.

XML açık bir standart olduğu için XML akışı gerektiğinde, platforma bakılmaksızın herhangi bir uygulama tarafından işlenebilir. XML Web Hizmetleri gibi ASP.NET kullanım kullanılarak oluşturulan <xref:System.Xml.Serialization.XmlSerializer> XML Web hizmeti uygulama Internet boyunca veya intranet arasında veri iletmek XML akışlarını oluşturmak için sınıf. Buna karşılık, seri durumundan çıkarma böyle bir XML akışı alır ve nesne yeniden oluşturur.

XML serileştirme SOAP belirtimine uygun XML akış içine nesneleri serileştirmek için de kullanılabilir. SOAP, XML, özellikle XML kullanarak yordam çağrılarını taşımak için tasarlanmış tabanlı bir protokoldür.

Serileştirmek veya seri durumdan nesneleri için kullanmak <xref:System.Xml.Serialization.XmlSerializer> sınıfı. Serileştirilecek sınıflar oluşturmak için XML şema tanımı aracını kullanın.

## <a name="in-this-section"></a>Bu Bölümde

[XML Serileştirmeye Giriş](introducing-xml-serialization.md)  
Genel bir tanımı serileştirme, özellikle XML serileştirme için sağlar.

[Nasıl yapılır: Bir nesneyi serileştirmek](how-to-serialize-an-object.md)  
Bir nesneyi serileştirmek için adım adım yönergeler sağlar.

[Nasıl yapılır: Bir nesneyi seri durumdan çıkarma](how-to-deserialize-an-object.md)  
Bir nesneyi seri durumdan çıkarmak için adım adım yönergeler sağlar.

[XML Serileştirme Örnekleri](examples-of-xml-serialization.md)  
XML serileştirme temelleri gösteren örnekleri sağlar.

[XML Şema Tanımı Aracı ve XML Serileştirme](the-xml-schema-definition-tool-and-xml-serialization.md)  
XML şema tanımı araç, belirli bir XML şeması tanım dili (XSD) şeması uyması sınıflar oluşturmak için veya bir .dll dosyasından bir XML şeması oluşturmak için nasıl kullanılacağını açıklar.

[Öznitelikleri Kullanarak XML Serileştirmeyi Denetleme](controlling-xml-serialization-using-attributes.md)  
Serileştirme öznitelikleri kullanarak denetlemek nasıl açıklar.

[XML Serileştirmeyi Denetleyen Öznitelikler](attributes-that-control-xml-serialization.md)  
XML serileştirme denetlemek için kullanılan öznitelikleri listeler.

[Nasıl yapılır: Bir XML Stream için alternatif öğe adı belirtin](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
Serileştirme geçersiz kılarak birden çok XML akışı oluşturmak nasıl gösteren Gelişmiş bir senaryo gösterir.

[Nasıl yapılır: Türetilen sınıfların serileştirmek denetimi](how-to-control-serialization-of-derived-classes.md)  
Türetilen sınıfların serileştirmek denetlemek nasıl bir örnek sağlar.

[Nasıl yapılır: XML öğesi ve XML öznitelik adlarını Sınıflandır](how-to-qualify-xml-element-and-xml-attribute-names.md)  
Tanımlamak ve hangi XML'de ad alanları XML akışında kullanılan şeklini denetlemek nasıl açıklar.

[XML Web Hizmetleri ile XML Serileştirme](xml-serialization-with-xml-web-services.md)  
XML serileştirme XML Web hizmetleri nasıl kullanıldığı açıklanmaktadır.

[Nasıl yapılır: Bir nesne bir SOAP kodlu XML Stream seri hale getirme](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
Nasıl kullanılacağını açıklar <xref:System.Xml.Serialization.XmlSerializer> başlıklı bölümüne World Wide Web Consortium (W3C) belgesinin 5 uygun kodlanmış SOAP XML akışlarını oluşturmak için sınıf [Basit Nesne Erişim Protokolü (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).

[Nasıl yapılır: Kodlanmış SOAP XML serileştirmesini geçersiz kılma](how-to-override-encoded-soap-xml-serialization.md)  
Nesneleri serileştirmek XML SOAP iletilerini olarak geçersiz kılma işlemini açıklar.

[Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler](attributes-that-control-encoded-soap-serialization.md)  
SOAP kodlu serileştirme denetlemek için kullanılan öznitelikleri listeler.

[\<system.xml.serialization> Element](system-xml-serialization-element.md)  
XML serileştirme denetlemek için üst düzey bir yapılandırma öğesi.

[\<dateTimeSerialization > öğesi](datetimeserialization-element.md)  
Serileştirme modunu denetler <xref:System.DateTime> nesneleri.

[\<schemaImporterExtensions > öğesi](schemaimporterextensions-element.md)  
Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfı.

[\<Ekle > öğesi için \<schemaImporterExtensions >](add-element-for-schemaimporterextensions.md)  
Tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfı.

## <a name="related-sections"></a>İlgili Bölümler

[ASP.NET ve XML Web hizmeti istemcileriyle kullanılarak oluşturulan XML Web Hizmetleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))  
Açıklayan ve ASP.NET kullanarak XML Web Hizmetleri program açıklayan konuları sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [İkili Serileştirme](binary-serialization.md)
