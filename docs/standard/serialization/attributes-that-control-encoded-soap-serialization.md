---
title: "Kodlanmış SOAP serileştirme denetim öznitelikleri"
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
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 358b635ee74699d9d427e8fac23fabd70c6cfa98
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>Kodlanmış SOAP serileştirme denetim öznitelikleri 
"Basit Nesne Erişim Protokolü (SOAP) 1.1" adlı World Wide Web Konsorsiyumu (www.w3.org) belgenin nasıl SOAP parametreleri kodlanmış açıklayan isteğe bağlı bir bölüm (Bölüm 5) içerir. Belirtimi 5 bölümüne uygun olması için bir özel bulunan öznitelikler kümesi kullanın <xref:System.Xml.Serialization> ad alanı. Bu öznitelik sınıfları ve sınıf üyeleri için uygun şekilde uygulayın ve ardından <xref:System.Xml.Serialization.XmlSerializer> sınıflar ve sınıf örneklerini serileştirmek için.  
  
 Aşağıdaki tabloda, bunlar uygulanabileceği, öznitelikleri ve ne yaptıklarını gösterir. Bu öznitelikler denetimine XML serileştirme kullanma hakkında daha fazla bilgi için bkz [nasıl yapılır: bir SOAP olarak bir nesneyi serileştirme-kodlanmış XML akışı](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) ve [nasıl yapılır: Kodlanmış SOAP XML serileştirme geçersiz kılma](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).  
  
 Öznitelikler hakkında daha fazla bilgi için bkz: [öznitelikleri](../../../docs/standard/attributes/index.md).  
  
|Öznitelik|Uygulandığı öğe:|Belirler|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Sınıf üyesi bir XML özniteliği olarak seri hale getirilir.|  
|<xref:System.Xml.Serialization.SoapElementAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Sınıf bir XML öğesi olarak seri hale.|  
|<xref:System.Xml.Serialization.SoapEnumAttribute>|Bir numaralandırma tanımlayıcı ortak alan.|Numaralandırma üyesi öğe adı.|  
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|Ortak özellikler ve alanları.|Kapsayan sınıfı serileştirilmiş olduğunda özellik veya alan yoksayılacak.|  
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|Genel türetilmiş sınıf bildirimleri ve Web Hizmetleri Açıklama Dili (WSDL) belgeleri için ortak yöntemleri.|Türü (serileştirilmiş olduğunda tanınması için) şemalar oluşturulurken dahil edilecek.|  
|<xref:System.Xml.Serialization.SoapTypeAttribute>|Ortak sınıf bildirimleri.|Sınıf bir XML türü olarak seri hale.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ve SOAP seri hale getirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Nasıl yapılır: bir SOAP kodlanmış XML akışı olarak bir nesneyi serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [Nasıl yapılır: Kodlanmış SOAP XML serileştirmesi için geçersiz kılma](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [Öznitelikleri](../../../docs/standard/attributes/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Nasıl yapılır: bir nesneyi serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Nasıl yapılır: bir nesne seri durumdan](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
