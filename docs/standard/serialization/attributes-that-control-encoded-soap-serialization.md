---
title: Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler
description: Bu makalede, System.Xml bulunan özel bir öznitelik kümesi listelenir. SOAP belirtimine uyması için serileştirme ad alanı gerekiyor.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 69a9d1c8734a393b576cf87e7e05ef92c10120c8
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282037"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler

[Basit nesne erişim Protokolü (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) adlı World WIDE Web KONSORSIYUMU (W3C) BELGESI, SOAP parametrelerinin nasıl kodlandığını açıklayan isteğe bağlı bir bölüm (5. bölüm) içerir. Belirtimin 5. bölümüne uymak için, ad alanında bulunan özel bir öznitelik kümesi kullanmanız gerekir <xref:System.Xml.Serialization> . Bu öznitelikleri sınıflar ve sınıfların üyelerine uygun şekilde uygulayın ve ardından <xref:System.Xml.Serialization.XmlSerializer> sınıfı veya sınıfların örneklerini seri hale getirmek için kullanın.

Aşağıdaki tabloda öznitelikleri, nerede uygulanabileceğini ve ne yaptığını gösterir. XML serileştirmesini denetlemek için bu öznitelikleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir nesneyi SOAP-Encoded XML akışı olarak serileştirme](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) ve [nasıl yapılır: kodlanmış SOAP XML serileştirmesini geçersiz kılma](how-to-override-encoded-soap-xml-serialization.md).

Öznitelikler hakkında daha fazla bilgi için bkz. [öznitelikler](../attributes/index.md).

|Öznitelik|Şunlara uygulanır|Belirler|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Sınıf üyesi bir XML özniteliği olarak serileştirilir.|
|<xref:System.Xml.Serialization.SoapElementAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Sınıf bir XML öğesi olarak seri hale.|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|Bir numaralandırma tanımlayıcı ortak alan.|Numaralandırma üyesi öğe adı.|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|Ortak özellikler ve alanları.|Kapsayan sınıfı serileştirilmiş olduğunda özellik veya alan yoksayılacak.|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|Genel türetilmiş sınıf bildirimleri ve Web Hizmetleri Açıklama Dili (WSDL) belgeleri için ortak yöntemleri.|Türü (serileştirilmiş olduğunda tanınması için) şemalar oluşturulurken dahil edilecek.|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|Ortak sınıf bildirimleri.|Sınıf bir XML türü olarak seri hale.|

## <a name="see-also"></a>Ayrıca bkz.

- [XML ve SOAP serileştirme](xml-and-soap-serialization.md)
- [Nasıl yapılır: SOAP Kodlu XML Akışı Olarak Nesneyi Serileştirme](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [Nasıl yapılır: Kodlanmış SOAP XML Serileştirmesini Geçersiz Kılma](how-to-override-encoded-soap-xml-serialization.md)
- [Öznitelikler](../attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Nasıl yapılır: Nesne Serileştirme](how-to-serialize-an-object.md)
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](how-to-deserialize-an-object.md)
