---
title: "XML serileştirme denetim öznitelikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes, serializing
- XmlSerializer class, serializing
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
- XML Schema, serializing
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b13a6f57cc0d6793e0bb5915c855a67355ed7a92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="attributes-that-control-xml-serialization"></a>XML serileştirme denetim öznitelikleri
Aşağıdaki tablodaki öznitelikleri sınıflar için geçerlidir ve sınıf üyeleri şekilde denetlemek için <xref:System.Xml.Serialization.XmlSerializer> serileştiren veya sınıfının bir örneği seri durumdan çıkarır. Bu öznitelikler XML serileştirme nasıl kontrol anlamak için bkz: [XML serileştirme kullanarak özniteliklerini denetleme](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md).  
  
 Bu öznitelikler, bir XML Web hizmeti tarafından oluşturulan değişmez değer stili SOAP iletileri denetlemek için de kullanılabilir. Bu öznitelikler bir XML Web Hizmetleri yöntemi uygulama hakkında daha fazla bilgi için bkz: [XML serileştirme XML Web Hizmetleri ile](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md).  
  
 Öznitelikler hakkında daha fazla bilgi için bkz: [öznitelikleri](../../../docs/standard/attributes/index.md).  
  
|Öznitelik|Uygulandığı öğe:|Belirler|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.XmlAnyAttributeAttribute>|Ortak alan, özelliği, parameTRe veya bir dizi döndürür dönüş değeri <xref:System.Xml.XmlAttribute> nesneleri.|İle seri durumdan çıkarılırken, dizi doldurulur <xref:System.Xml.XmlAttribute> bilinmeyen tüm XML öznitelikleri şemaya temsil eden nesne.|  
|<xref:System.Xml.Serialization.XmlAnyElementAttribute>|Ortak alan, özelliği, parameTRe veya bir dizi döndürür dönüş değeri <xref:System.Xml.XmlElement> nesneleri.|İşlenirken, dizi renkle doldurulup <xref:System.Xml.XmlElement> şemaya bilinmeyen tüm XML öğeleri temsil eden nesneleri.|  
|<xref:System.Xml.Serialization.XmlArrayAttribute>|Ortak alan, özelliği, parameTRe veya karmaşık nesneler dizisi döndürür dönüş değeri.|Dizi üyelerinin bir XML dizi üyeleri olarak oluşturulur.|  
|<xref:System.Xml.Serialization.XmlArrayItemAttribute>|Ortak alan, özelliği, parameTRe veya karmaşık nesneler dizisi döndürür dönüş değeri.|Bir diziye eklenen türetilen türler. Genellikle birlikte uygulanan bir <xref:System.Xml.Serialization.XmlArrayAttribute>.|  
|<xref:System.Xml.Serialization.XmlAttributeAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Üye bir XML özniteliği olarak seri hale getirilir.|  
|<xref:System.Xml.Serialization.XmlChoiceIdentifierAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Üye numaralandırması kullanarak daha fazla disambiguated.|  
|<xref:System.Xml.Serialization.XmlElementAttribute>|Ortak alan, özelliği, parameTRe veya dönüş değeri.|Alanı veya özelliği bir XML öğesi olarak seri hale.|  
|<xref:System.Xml.Serialization.XmlEnumAttribute>|Bir numaralandırma tanımlayıcı ortak alan.|Numaralandırma üyesi öğe adı.|  
|<xref:System.Xml.Serialization.XmlIgnoreAttribute>|Ortak özellikler ve alanları.|Kapsayan sınıfı serileştirilmiş olduğunda özellik veya alan yoksayılacak.|  
|<xref:System.Xml.Serialization.XmlIncludeAttribute>|Genel sınıf bildirimleri ve Web Hizmetleri Açıklama Dili (WSDL) belgeleri için ortak yöntemleri dönüş değerleri türetilmiş.|Sınıf (serileştirilmiş olduğunda tanınması için) şemalar oluşturulurken dahil edilecek.|  
|<xref:System.Xml.Serialization.XmlRootAttribute>|Ortak sınıf bildirimleri.|Öznitelik hedef XML serileştirme bir XML kök öğesi olarak denetler. Öznitelik, daha fazla ad alanı ve öğe adı belirtmek için kullanın.|  
|<xref:System.Xml.Serialization.XmlTextAttribute>|Ortak özellikler ve alanları.|Özellik veya alan XML metin olarak serileştirilmiş.|  
|<xref:System.Xml.Serialization.XmlTypeAttribute>|Ortak sınıf bildirimleri.|XML ad alanı ve adını yazın.|  
  
 Bu öznitelikler yanı sıra tüm bulunduğu içinde <xref:System.Xml.Serialization> ad alanı, aynı zamanda uygulayabilirsiniz <xref:System.ComponentModel.DefaultValueAttribute> özniteliği bir alan. **DefaultValueAttribute** herhangi bir değer belirtilirse, otomatik olarak üyesine atanacak değeri ayarlar.  
  
 Kodlanmış SOAP XML serileştirme denetlemek için bkz: [öznitelikleri, Denetim kodlanmış SOAP seri hale getirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ve SOAP seri hale getirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [XML serileştirme özniteliklerini kullanarak denetleme](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [Nasıl yapılır: bir XML akışı için bir diğer öğe adı belirtin](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 [Nasıl yapılır: bir nesneyi serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Nasıl yapılır: bir nesne seri durumdan](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
