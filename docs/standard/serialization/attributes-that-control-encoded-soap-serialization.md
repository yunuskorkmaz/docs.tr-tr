---
title: Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 2961d9abc6c32e78b5a61e8f2bbea5cfcf6677bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794946"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler

[Basit nesne erişim Protokolü (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) adlı World WIDE Web KONSORSIYUMU (W3C) BELGESI, SOAP parametrelerinin nasıl kodlandığını açıklayan isteğe bağlı bir bölüm (5. bölüm) içerir. Belirtimin 5. bölümüne uymak için, <xref:System.Xml.Serialization> ad alanında bulunan özel bir öznitelik kümesi kullanmanız gerekir. Bu öznitelikleri sınıflar ve sınıfların üyelerine uygun şekilde uygulayın ve ardından sınıfı veya sınıfların örneklerini seri <xref:System.Xml.Serialization.XmlSerializer> hale getirmek için kullanın.

Aşağıdaki tabloda öznitelikleri, nerede uygulanabileceğini ve ne yaptığını gösterir. XML serileştirmesini denetlemek için bu öznitelikleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir NESNEYI SOAP kodlu XML akışı olarak serileştirme](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) ve [nasıl yapılır: kodlanmış SOAP XML serileştirmesini geçersiz kılma](how-to-override-encoded-soap-xml-serialization.md).

Öznitelikler hakkında daha fazla bilgi için bkz. [öznitelikler](../../../docs/standard/attributes/index.md).

|Öznitelik|Uygulandığı öğe:|Belirler|
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
- [Öznitelikler](../../../docs/standard/attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Nasıl yapılır: Nesne Serileştirme](how-to-serialize-an-object.md)
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](how-to-deserialize-an-object.md)
