---
title: "Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98eb46e0f31995efe7db177d90691a9f59288590
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]kullanan <xref:System.Runtime.Serialization.DataContractSerializer> veri XML'e dönüştürecek ve XML verilerine geri dönüştürmek için kendi varsayılan seri hale getirme altyapısı olarak. <xref:System.Runtime.Serialization.DataContractSerializer> Serileştirmek için tasarlanmış *veri sözleşmesi* türleri. Ancak, bir örtük veri sözleşmesi sahip olarak düşünülebilir birçok diğer türleri, destekler. Seri hale getirilebilir türlerinin tam bir listesi verilmiştir:  
  
-   Parametrelere sahip olmayan bir oluşturucuya sahip tüm herkese görünür türleri.  
  
-   Veri türleri sözleşme. Türlerini bunlar <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği uygulandı. İş nesneleri temsil eden yeni özel türler anlaşma türleri normal veri olarak oluşturulmalıdır. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri sözleşmelerini kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) ve [seri hale getirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
-   Koleksiyon türleri. Bunlar veri listeleri temsil eden türleridir. Bunlar normal diziler türlerin veya koleksiyon türleri gibi olabilir <xref:System.Collections.ArrayList> ve <xref:System.Collections.Generic.Dictionary%602>. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Özniteliği, bu tür serileştirme özelleştirmek için kullanılabilir, ancak gerekli değildir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri sözleşmelerinde koleksiyon türleri](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
  
-   Numaralandırma türleri. Numaralandırmalar bayrağı numaralandırmalar dahil olmak üzere, seri hale getirilebilir. İsteğe bağlı olarak, numaralandırma türleri ile işaretlenebilir <xref:System.Runtime.Serialization.DataContractAttribute> serileştirmede katılan her üye olarak gerekir; bu durumda, öznitelik <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği. İşaretlenmemiş üyeleri seri değildir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri sözleşmelerinde Numaralandırma türleri](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
-   .NET framework ilkel türler. .NET Framework'e yerleştirilmiş aşağıdaki türleri tüm serileştirilebilir ve ilkel türler olduğu kabul edilir: <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Boolean>, <xref:System.Char>, <xref:System.Decimal>, <xref:System.Object>, ve <xref:System.String>.  
  
-   Başka ilkel türler. Bu tür .NET Framework'teki temelleri değildir ancak serileştirilmiş XML biçiminde temelleri olarak kabul edilir. Bu türleri <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>, <xref:System.Xml.XmlQualifiedName>ve dizileri <xref:System.Byte>.  
  
    > [!NOTE]
    >  Başka ilkel türler aksine <xref:System.DateTimeOffset> varsayılan olarak bilinen bir tür değil. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri sözleşmesi bilinen türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)).  
  
-   Türleri ile işaretlenen <xref:System.SerializableAttribute> özniteliği. Dahil birçok türleri [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] temel sınıf kitaplığı sonbaharda bu kategoriyi içine. <xref:System.Runtime.Serialization.DataContractSerializer> Tam olarak .NET Framework remoting tarafından kullanılan bu serileştirme programlama modelini destekleyen <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, desteği dahil olmak üzere <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
-   Ham XML veya temsil eden türlerin temsil eden türlerin [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] ilişkisel veri. <xref:System.Xml.XmlElement> Ve dizi <xref:System.Xml.XmlNode> türleri XML doğrudan temsil eden bir yolu desteklenir. Ayrıca, bu uygulama türleri <xref:System.Xml.Serialization.IXmlSerializable> arabirimi desteklenir, ilgili dahil olmak üzere <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliği ve <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement> türleri. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataTable> Türü ve <xref:System.Data.DataSet> türü (yazılan türetilmiş sınıflarının yanı sıra) tüm uygulama <xref:System.Xml.Serialization.IXmlSerializable> arabirimi ve bu nedenle bu kategoriye sığmayacak. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][XML ve ADO.NET türleri veri sözleşmelerinde](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Kısmi belirli türleri kullanma sınırlamaları güven modu  
 Aşağıdaki sınırlamalar belirli türleri kısmi güven modu senaryolarda kullanırken listesidir:  
  
-   Serileştirmek veya seri durumdan uygulayan bir tür için <xref:System.Runtime.Serialization.ISerializable> kısmen güvenilen kod kullanarak <xref:System.Runtime.Serialization.DataContractSerializer> gerektirir <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> ve <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> izinleri.  
  
-   Çalıştırırken [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kod [kısmi güven](../../../../docs/framework/wcf/feature-details/partial-trust.md) modu, seri hale getirme ve seri durumdan çıkarma işlemi `readonly` alanlar (her ikisi de `public` ve `private`) desteklenmiyor. Oluşturulan IL doğrulanamaz olduğundan ve bu nedenle, yükseltilmiş izinler gerektirir budur.  
  
-   Hem <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> bir kısmi güven ortamında desteklenir. Ancak, kullanım <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki koşullara tabi olan:  
  
    -   Tüm serileştirilebilir `[DataContract]` türleri ortak olmalıdır.  
  
    -   Tüm serileştirilebilir `[DataMember]` alanları veya özelliklerinde bir `[DataContract]` türü ortak ve gerekir okuma/yazma. Seri hale getirme ve seri durumdan çıkarma işlemi `readonly` çalıştırırken alanları desteklenmiyor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kısmen güvenilen uygulamada.  
  
    -   `[Serializable]` / `ISerializable]` Programlama modeli bir kısmi güven ortamında desteklenmez.  
  
    -   Kod veya makine düzeyinde yapılandırma türleri'nin belirtilmesi gerekir bilinen (`Machine.config`). Bilinen türler güvenlik nedenleriyle uygulama düzeyi yapılandırmasında belirtilemez.  
  
-   Türleri uygulayan <xref:System.Runtime.Serialization.IObjectReference> nedeniyle kısmen güvenilen bir ortamda bir özel durum <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> gerektirdiğine güvenlik izni `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`.  
  
## <a name="additional-notes-on-serialization"></a>Seri hale getirme ilişkin ek notlar  
 Aşağıdaki kuralları veri sözleşmesi seri hale getirici tarafından desteklenen türleri için de geçerlidir:  
  
-   Genel türler veri sözleşmesi seri hale getirici tarafından tam olarak desteklenir.  
  
-   Boş değer atanabilir türler veri sözleşmesi seri hale getirici tarafından tam olarak desteklenir.  
  
-   Arabirim türlerini kabul edilir ya da olarak <xref:System.Object> veya koleksiyon türleri olarak koleksiyon arabirimleri söz konusu olduğunda.  
  
-   Yapılar ve sınıflar desteklenir.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Tarafından kullanılan programlama modelini desteklemiyor <xref:System.Xml.Serialization.XmlSerializer> ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri. Özellikle, gibi öznitelikleri desteklemiyor <xref:System.Xml.Serialization.XmlElementAttribute> ve <xref:System.Xml.Serialization.XmlAttributeAttribute>. Bu programlama modeli desteğini etkinleştirmek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanmak geçirilmesi gerekiyor <xref:System.Xml.Serialization.XmlSerializer> yerine <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
-   <xref:System.DBNull> Türü, özel bir yolla değerlendirilir. Bir singleton türü ise ve seri durumdan çıkarma sırasında seri durumdan çıkarıcının singleton kısıtlamayla uyar ve tüm işaret `DBNull` singleton örneğine başvuru. Çünkü `DBNull` , talep serializable bir tür olduğundan <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> izni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Anlaşmalarında XML ve ADO.NET Türleri](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)  
 [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Seri Hale Getirilebilir Türler](../../../../docs/framework/wcf/feature-details/serializable-types.md)  
 [Veri Anlaşmalarında Koleksiyon Türleri](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)  
 [Veri Anlaşmalarında Sabit Listesi Türleri](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)
