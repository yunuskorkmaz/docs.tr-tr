---
title: Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: 9c532858ba3b93d427e5c0455f953db2499ebd6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072551"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler
Windows Communication Foundation (WCF) kullanan <xref:System.Runtime.Serialization.DataContractSerializer> XML verileri dönüştürmek için ve XML geri verisine dönüştüremedi, varsayılan seri hale getirme altyapısı olarak. <xref:System.Runtime.Serialization.DataContractSerializer> Seri hale getirmek için tasarlanan *veri anlaşması* türleri. Ancak, bir örtük veri anlaşması sahip olduğu düşünülebilir birçok diğer türleri destekler. Seri hale getirilebilir türlerin tam listesi verilmiştir:  
  
-   Parametreleri olmayan bir oluşturucuya sahip tüm herkese görünür türler.  
  
-   Veri sözleşmesi türleri. Bunlar türlerini <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği uygulandı. İş nesnelerini temsil eden yeni bir özel türler normalde sözleşmesi türleri veri oluşturulmalıdır. Daha fazla bilgi için [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) ve [Serializable türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
-   Koleksiyon türleri. Bunlar veri listeleri temsil eden türleridir. Bunlar normal dizilerin türleri veya koleksiyon türleri gibi olabilir <xref:System.Collections.ArrayList> ve <xref:System.Collections.Generic.Dictionary%602>. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Özniteliği, bu türlerin seri hale getirme özelleştirmek için kullanılabilir ancak gerekli değildir. Daha fazla bilgi için [veri anlaşmalarında koleksiyon türleri](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
  
-   Numaralandırma türleri. Bayrak sabit listeleri, dahil olmak üzere sabit listeleri, seri hale getirilebilir. Numaralandırma türleri ile isteğe bağlı olarak işaretlenebilir <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği, bu durumda serileştirme katılan her üyesi ile işaretlenmelidir <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği. İşaretlenmemiş üyeleri seri duruma getirilmez. Daha fazla bilgi için [veri sözleşmelerinde Numaralandırma türleri](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
-   .NET framework ilkel türleri. .NET Framework'e yerleşik aşağıdaki türleri tüm seri hale getirilebilir ve basit türler olarak değerlendirilir: <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Boolean>, <xref:System.Char>, <xref:System.Decimal>, <xref:System.Object>, ve <xref:System.String>.  
  
-   Diğer ilkel türler. Bu tür, .NET Framework ilkel değildir ancak temelleri serileştirilmiş XML biçiminde olarak kabul edilir. Bu türler <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>, <xref:System.Xml.XmlQualifiedName>ve dizileri <xref:System.Byte>.  
  
    > [!NOTE]
    >  Diğer ilkel türler, aksine <xref:System.DateTimeOffset> varsayılan olarak bilinen bir tür değil. Daha fazla bilgi için [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)).  
  
-   Türleri ile işaretlenen <xref:System.SerializableAttribute> özniteliği. Dahil birçok türü [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] temel sınıf kitaplığı bu kategoriye ayrılır. <xref:System.Runtime.Serialization.DataContractSerializer> Tam .NET Framework uzaktan iletişim tarafından kullanılan bu serileştirme programlama modelini destekler <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, desteği dahil olmak üzere <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
-   Ham XML veya temsil eden türleri temsil eden türleri [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] ilişkisel veriler. <xref:System.Xml.XmlElement> Ve dizi <xref:System.Xml.XmlNode> türleri, doğrudan XML temsil eden bir yol desteklenir. Ayrıca, uygulayan türleri <xref:System.Xml.Serialization.IXmlSerializable> arabirimi desteklenir, ilgili dahil olmak üzere <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliği ve <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement> türleri. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]<xref:System.Data.DataTable> Türü ve <xref:System.Data.DataSet> türü (yazılan türetilmiş sınıflarının yanı sıra) tüm uygulama <xref:System.Xml.Serialization.IXmlSerializable> arabirim ve bu nedenle bu kategoriye uygun. Daha fazla bilgi için [XML ve ADO.NET türleri veri anlaşmalarında](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Kısmi belirli türlerini kullanma sınırlamaları güven modu  
 Kısıtlamaların listesi belirli türlerini kısmi güven modu senaryolarda kullanırken verilmiştir:  
  
-   Serileştirmek veya seri durumdan uygulayan bir tür için <xref:System.Runtime.Serialization.ISerializable> kısmen güvenilen kod kullanarak <xref:System.Runtime.Serialization.DataContractSerializer> gerektirir <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> ve <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> izinleri.  
  
-   WCF kod çalıştırırken [kısmi güven](../../../../docs/framework/wcf/feature-details/partial-trust.md) modu, serileştirme ve seri durumdan çıkarma `readonly` alanları (her ikisi de `public` ve `private`) desteklenmiyor. Oluşturulan IL doğrulanamaz ve bu nedenle, yükseltilmiş izinler gerektirir olmasıdır.  
  
-   Hem <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> kısmi güven ortamında desteklenir. Ancak, kullanım <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki koşullara tabi olan:  
  
    -   Tüm serileştirilebilir `[DataContract]` türler genel olmalıdır.  
  
    -   Tüm serileştirilebilir `[DataMember]` alanlar ve özellikler bir `[DataContract]` türü genel olmalıdır ve okuma/yazma. Serileştirme ve seri durumundan çıkarma `readonly` WCF kısmen güvenilen bir uygulamada çalışırken alanları desteklenmiyor.  
  
    -   `[Serializable]` / `ISerializable]` Programlama modeli, kısmi güven ortamında desteklenmez.  
  
    -   Bilinen türleri, kod veya makine düzeyinde yapılandırma belirtilmelidir (`Machine.config`). Uygulama düzeyinde yapılandırma güvenlik nedenleriyle, bilinen türleri belirtilemez.  
  
-   Türleri uygulayan <xref:System.Runtime.Serialization.IObjectReference> kısmen güvenilen bir ortamda, çünkü bir özel durum <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> gerektirdiğine güvenlik izni `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`.  
  
## <a name="additional-notes-on-serialization"></a>Serileştirme hakkında ek notlar  
 Veri sözleşme seri hale getirici tarafından desteklenen türler de aşağıdaki kurallar geçerlidir:  
  
-   Genel türler, veri sözleşme seri hale getirici tarafından tam olarak desteklenir.  
  
-   Boş değer atanabilir türler, veri sözleşme seri hale getirici tarafından tam olarak desteklenir.  
  
-   Arabirim türlerinde kabul edilir ya da farklı <xref:System.Object> veya koleksiyon türleri olarak koleksiyon arabirimleri.  
  
-   Yapılar ve sınıflar hem desteklenir.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Tarafından kullanılan programlama modelini desteklemiyor <xref:System.Xml.Serialization.XmlSerializer> ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri. Özellikle, gibi öznitelikleri desteklemiyor <xref:System.Xml.Serialization.XmlElementAttribute> ve <xref:System.Xml.Serialization.XmlAttributeAttribute>. Bu programlama modeli desteğini etkinleştirmek için WCF kullanmaya geçiş gerekir <xref:System.Xml.Serialization.XmlSerializer> yerine <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
-   <xref:System.DBNull> Türü özel bir şekilde kabul edilir. Singleton türüdür ve seri durumundan çıkarma sırasında seri durumdan çıkarıcı tekil kısıtlaması uyar ve tüm işaret `DBNull` tekil örneğini başvuruları. Çünkü `DBNull` gerektirmesi seri hale getirilebilir bir tür olduğunda <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> izni.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Sözleşmelerinde XML ve ADO.NET Türleri](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)
- [Veri Sözleşmelerini Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Seri Hale Getirilebilir Türler](../../../../docs/framework/wcf/feature-details/serializable-types.md)
- [Veri Sözleşmelerinde Koleksiyon Türleri](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)
- [Veri Sözleşmelerinde Numaralandırma Türleri](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)
