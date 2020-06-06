---
title: XML Serileştirmeyi Denetleyen Öznitelikler
description: Bu makale, kaynak ve sınıf üyeleri için uygulayabileceğiniz ve XmlSerializer 'ın bir sınıf örneğini serileştirerek veya seri durumdan ayırmayı denetleyen öznitelikler içerir.
ms.date: 03/30/2017
helpviewer_keywords:
- classes, serializing
- XmlSerializer class, serializing
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
- XML Schema, serializing
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
ms.openlocfilehash: fbc42ff696107f4a1b06d3611fc97a09cc4a3542
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84276705"
---
# <a name="attributes-that-control-xml-serialization"></a>XML Serileştirmeyi Denetleyen Öznitelikler
Sınıfının bir örneğini seri hale getirmenin veya seri hale getirmenin yolunu denetlemek için aşağıdaki tablodaki öznitelikleri sınıflar ve sınıf üyelerine uygulayabilirsiniz <xref:System.Xml.Serialization.XmlSerializer> . Bu özniteliklerin XML serileştirmesini denetlemesini anlamak için bkz. [öznitelikleri kullanarak XML serileştirmesini denetleme](controlling-xml-serialization-using-attributes.md).  
  
 Bu öznitelikler, bir XML Web hizmeti tarafından oluşturulan SOAP iletilerini denetlemek için de kullanılabilir. Bu öznitelikleri bir XML Web Hizmetleri yöntemine uygulama hakkında daha fazla bilgi için bkz. xml [Web Hizmetleri Ile XML serileştirme](xml-serialization-with-xml-web-services.md).  
  
 Öznitelikler hakkında daha fazla bilgi için bkz. [öznitelikler](../attributes/index.md).  
  
|Öznitelik|Şunlara uygulanır|Belirler|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.XmlAnyAttributeAttribute>|Ortak alan, özelliği, parameTRe veya bir dizi döndürür dönüş değeri <xref:System.Xml.XmlAttribute> nesneleri.|Seri durumdan çıkarılırken, dizi, <xref:System.Xml.XmlAttribute> şemaya bilinmeyen tüm XML özniteliklerini temsil eden nesneleriyle doldurulur.|  
|<xref:System.Xml.Serialization.XmlAnyElementAttribute>|Ortak alan, özelliği, parameTRe veya bir dizi döndürür dönüş değeri <xref:System.Xml.XmlElement> nesneleri.|İşlenirken, dizi renkle doldurulup <xref:System.Xml.XmlElement> şemaya bilinmeyen tüm XML öğeleri temsil eden nesneleri.|  
|<xref:System.Xml.Serialization.XmlArrayAttribute>|Ortak alan, özelliği, parameTRe veya karmaşık nesneler dizisi döndürür dönüş değeri.|Dizi üyelerinin bir XML dizi üyeleri olarak oluşturulur.|  
|<xref:System.Xml.Serialization.XmlArrayItemAttribute>|Ortak alan, özelliği, parameTRe veya karmaşık nesneler dizisi döndürür dönüş değeri.|Bir diziye eklenen türetilen türler. Genellikle birlikte uygulanan bir <xref:System.Xml.Serialization.XmlArrayAttribute>.|  
|<xref:System.Xml.Serialization.XmlAttributeAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Üye bir XML özniteliği olarak serileştirilir.|  
|<xref:System.Xml.Serialization.XmlChoiceIdentifierAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Üye numaralandırması kullanarak daha fazla disambiguated.|  
|<xref:System.Xml.Serialization.XmlElementAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Alanı veya özelliği bir XML öğesi olarak seri hale.|  
|<xref:System.Xml.Serialization.XmlEnumAttribute>|Bir numaralandırma tanımlayıcı ortak alan.|Numaralandırma üyesi öğe adı.|  
|<xref:System.Xml.Serialization.XmlIgnoreAttribute>|Ortak özellikler ve alanları.|Kapsayan sınıfı serileştirilmiş olduğunda özellik veya alan yoksayılacak.|  
|<xref:System.Xml.Serialization.XmlIncludeAttribute>|Genel sınıf bildirimleri ve Web Hizmetleri Açıklama Dili (WSDL) belgeleri için ortak yöntemleri dönüş değerleri türetilmiş.|Sınıf (serileştirilmiş olduğunda tanınması için) şemalar oluşturulurken dahil edilecek.|  
|<xref:System.Xml.Serialization.XmlRootAttribute>|Ortak sınıf bildirimleri.|XML kök öğesi olarak öznitelik hedefinin XML serileştirmesini denetler. Ad alanı ve öğe adını daha fazla belirtmek için özniteliğini kullanın.|  
|<xref:System.Xml.Serialization.XmlTextAttribute>|Ortak özellikler ve alanları.|Özellik veya alan XML metin olarak serileştirilmiş.|  
|<xref:System.Xml.Serialization.XmlTypeAttribute>|Ortak sınıf bildirimleri.|XML ad alanı ve adını yazın.|  
  
 Ad alanında bulunan bu özniteliklerin yanı sıra <xref:System.Xml.Serialization> , <xref:System.ComponentModel.DefaultValueAttribute> bir alana özniteliği de uygulayabilirsiniz. **DefaultValueAttribute** değeri belirtilmemişse, üyeye otomatik olarak atanacak değeri ayarlar.  
  
 Kodlanmış SOAP XML serileştirmesini denetlemek için bkz. [KODLANMıŞ SOAP serileştirmesini denetleyen öznitelikler](attributes-that-control-encoded-soap-serialization.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ve SOAP serileştirme](xml-and-soap-serialization.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Öznitelikleri Kullanarak XML Serileştirmeyi Denetleme](controlling-xml-serialization-using-attributes.md)
- [Nasıl yapılır: XML Akışı için Alternatif Öğe Adı Belirtme](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [Nasıl yapılır: Nesne Serileştirme](how-to-serialize-an-object.md)
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](how-to-deserialize-an-object.md)
