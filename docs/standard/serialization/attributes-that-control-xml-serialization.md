---
title: XML serileştirme denetleyen öznitelikler
ms.date: 03/30/2017
helpviewer_keywords:
- classes, serializing
- XmlSerializer class, serializing
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
- XML Schema, serializing
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
ms.openlocfilehash: 4acc17db83817d5aa78c9a91bfdac4e775de3743
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038156"
---
# <a name="attributes-that-control-xml-serialization"></a>XML serileştirme denetleyen öznitelikler
Aşağıdaki tablodaki öznitelikleri için sınıflar uygulanır ve sınıf üyeleri yolla denetlemek için <xref:System.Xml.Serialization.XmlSerializer> serileştiren veya sınıfının bir örneği seri durumdan çıkarır. Bu öznitelikler XML serileştirme nasıl kontrol anlamak için bkz [XML serileştirme kullanarak özniteliklerini denetleme](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md).  
  
 Bu öznitelikler, bir XML Web hizmeti tarafından oluşturulan değişmez değer stil SOAP iletilerini denetlemek için de kullanılabilir. Bu öznitelikler bir XML Web Hizmetleri yöntemi uygulama hakkında daha fazla bilgi için bkz. [XML serileştirme XML Web Hizmetleri ile](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md).  
  
 Öznitelikler hakkında daha fazla bilgi için bkz. [öznitelikleri](../../../docs/standard/attributes/index.md).  
  
|Öznitelik|Uygulandığı öğe:|Belirler|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.XmlAnyAttributeAttribute>|Ortak alan, özelliği, parameTRe veya bir dizi döndürür dönüş değeri <xref:System.Xml.XmlAttribute> nesneleri.|İle işlenirken, dizi doldurulacaktır <xref:System.Xml.XmlAttribute> şemaya bilinmeyen tüm XML özniteliklerini temsil eden nesneleri.|  
|<xref:System.Xml.Serialization.XmlAnyElementAttribute>|Ortak alan, özelliği, parameTRe veya bir dizi döndürür dönüş değeri <xref:System.Xml.XmlElement> nesneleri.|İşlenirken, dizi renkle doldurulup <xref:System.Xml.XmlElement> şemaya bilinmeyen tüm XML öğeleri temsil eden nesneleri.|  
|<xref:System.Xml.Serialization.XmlArrayAttribute>|Ortak alan, özelliği, parameTRe veya karmaşık nesneler dizisi döndürür dönüş değeri.|Dizi üyelerinin bir XML dizi üyeleri olarak oluşturulur.|  
|<xref:System.Xml.Serialization.XmlArrayItemAttribute>|Ortak alan, özelliği, parameTRe veya karmaşık nesneler dizisi döndürür dönüş değeri.|Bir diziye eklenen türetilen türler. Genellikle birlikte uygulanan bir <xref:System.Xml.Serialization.XmlArrayAttribute>.|  
|<xref:System.Xml.Serialization.XmlAttributeAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Üye bir XML özniteliği olarak seri hale.|  
|<xref:System.Xml.Serialization.XmlChoiceIdentifierAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Üye numaralandırması kullanarak daha fazla disambiguated.|  
|<xref:System.Xml.Serialization.XmlElementAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Alanı veya özelliği bir XML öğesi olarak seri hale.|  
|<xref:System.Xml.Serialization.XmlEnumAttribute>|Bir numaralandırma tanımlayıcı ortak alan.|Numaralandırma üyesi öğe adı.|  
|<xref:System.Xml.Serialization.XmlIgnoreAttribute>|Ortak özellikler ve alanları.|Kapsayan sınıfı serileştirilmiş olduğunda özellik veya alan yoksayılacak.|  
|<xref:System.Xml.Serialization.XmlIncludeAttribute>|Genel sınıf bildirimleri ve Web Hizmetleri Açıklama Dili (WSDL) belgeleri için ortak yöntemleri dönüş değerleri türetilmiş.|Sınıf (serileştirilmiş olduğunda tanınması için) şemalar oluşturulurken dahil edilecek.|  
|<xref:System.Xml.Serialization.XmlRootAttribute>|Ortak sınıf bildirimleri.|XML özniteliği hedef serileştirmek bir XML kök öğesi olarak denetler. Öznitelik, daha fazla ad alanı ve öğe adını belirtmek için kullanın.|  
|<xref:System.Xml.Serialization.XmlTextAttribute>|Ortak özellikler ve alanları.|Özellik veya alan XML metin olarak serileştirilmiş.|  
|<xref:System.Xml.Serialization.XmlTypeAttribute>|Ortak sınıf bildirimleri.|XML ad alanı ve adını yazın.|  
  
 Ek olarak bu öznitelikler, hangi tüm içinde bulunan <xref:System.Xml.Serialization> ad alanı, aynı zamanda uygulayabileceğiniz <xref:System.ComponentModel.DefaultValueAttribute> özniteliği için bir alan. **DefaultValueAttribute** herhangi bir değer belirtilirse bu üye için otomatik olarak atanır değeri ayarlar.  
  
 Kodlanmış SOAP XML serileştirme denetlemek için bkz: [öznitelikleri emin denetim kodlanmış SOAP serileştirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
- <xref:System.Xml.Serialization.XmlSerializer>  
- [Öznitelikleri Kullanarak XML Serileştirmeyi Denetleme](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
- [Nasıl yapılır: XML Akışı için Alternatif Öğe Adı Belirtme](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
- [Nasıl yapılır: Nesne Serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
