---
title: Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: f3eedda6c9493688680099f4b07810aebf69ff8a
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249467"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler

Windows Communication Foundation (WCF), verileri XML'ye dönüştürmek ve XML'i tekrar veriye dönüştürmek için varsayılan serileştirme altyapısı <xref:System.Runtime.Serialization.DataContractSerializer> olarak kullanır. Veri <xref:System.Runtime.Serialization.DataContractSerializer> *sözleşmesi* türlerini seri hale getirmek için tasarlanmıştır. Ancak, örtük bir veri sözleşmesi ne olduğu düşünülebilir diğer birçok türleri destekler. Serileştirilebilen türlerin tam listesi aşağıda verilmiştir:

- Parametreleri olmayan bir oluşturucusu olan tüm genel olarak görünür türleri.

- Veri sözleşmesi türleri. Bunlar özniteliğin <xref:System.Runtime.Serialization.DataContractAttribute> uygulandığı türlerdir. İş nesnelerini temsil eden yeni özel türleri normalde veri sözleşmesi türleri olarak oluşturulmalıdır. Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md)

- Toplama türleri. Bunlar veri listelerini temsil eden türlerdir. Bunlar, düzenli tür dizileri veya koleksiyon türleri <xref:System.Collections.ArrayList> <xref:System.Collections.Generic.Dictionary%602>olabilir. Öznitelik <xref:System.Runtime.Serialization.CollectionDataContractAttribute> bu tür serileştirme özelleştirmek için kullanılabilir, ancak gerekli değildir. Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)

- Numaralandırma türleri. Bayrak sayısallaştırmaları da dahil olmak üzere sayısallaştırmalar serileştirilebilir. İsteğe bağlı olarak, numaralandırma türleri <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik ile işaretlenebilir, bu durumda serileştirmeye katılan her <xref:System.Runtime.Serialization.EnumMemberAttribute> üye öznitelik ile işaretlenmiş olmalıdır. İşaretlenmemiş üyeler seri hale getirilmeyecektir. Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)

- .NET Framework ilkel türleri. .NET Framework'de yerleşik olarak yer alan aşağıdaki türler seri hale <xref:System.Byte> <xref:System.SByte>getirilebilir ve ilkel tipler olarak <xref:System.Decimal> <xref:System.Object>kabul <xref:System.String>edilir: , , <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.UInt16> <xref:System.UInt32> <xref:System.UInt64> <xref:System.Single> <xref:System.Double> <xref:System.Boolean> <xref:System.Char>, , , , , , , ve .

- Diğer ilkel tipler. Bu türler .NET Framework'de ilkel değildir, ancak serixml formunda ilkel olarak kabul edilir. Bu tür <xref:System.DateTime> <xref:System.DateTimeOffset>, <xref:System.TimeSpan> <xref:System.Guid>, <xref:System.Uri> <xref:System.Xml.XmlQualifiedName>, , , <xref:System.Byte>, , ve dizileri .

  > [!NOTE]
  > Diğer ilkel türlerin <xref:System.DateTimeOffset> aksine, varsayılan olarak bilinen bir tür değildir. Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)

- Öznitelik ile <xref:System.SerializableAttribute> işaretlenmiş türleri. .NET Framework taban sınıf kitaplığında yer alan birçok tür bu kategoriye girer. .NET <xref:System.Runtime.Serialization.DataContractSerializer> Framework remoting tarafından kullanılan bu serileştirme programlama modelini <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> <xref:System.Runtime.Serialization.ISerializable> tam olarak destekler, ve arayüz desteği de dahil olmak üzere.

- Ham XML'i veya ADO.NET ilişkisel verileri temsil eden türleri temsil eden türler. Ve <xref:System.Xml.XmlElement> türleri <xref:System.Xml.XmlNode> dizi doğrudan XML temsil eden bir yolu olarak desteklenir. Ayrıca, <xref:System.Xml.Serialization.IXmlSerializable> arabirimi uygulayan türler, ilgili <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> öznitelik ve <xref:System.Xml.Linq.XDocument> türleri <xref:System.Xml.Linq.XElement> de dahil olmak üzere desteklenir. ADO.NET<xref:System.Data.DataTable> türü ve <xref:System.Data.DataSet> türü (yanı sıra, türtintin <xref:System.Xml.Serialization.IXmlSerializable> sınıflar) tüm arabirimi uygulamak ve bu nedenle bu kategoriye uygun. Daha fazla bilgi için [ADO.NET](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)bkz.

## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Kısmi Güven Modunda Belirli Türleri Kullanmanın Sınırlamaları

Kısmi güven modu senaryolarında belirli türleri kullanırken sınırlamalar listesi aşağıda verilmiştir:

- <xref:System.Runtime.Serialization.DataContractSerializer> Gerektiren <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> izinleri <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> kullanarak kısmen güvenilen <xref:System.Runtime.Serialization.ISerializable> kodda uygulayan bir türü serihale getirmek veya deserialize etmek.

- [Kısmi Güven](../../../../docs/framework/wcf/feature-details/partial-trust.md) modunda WCF kodu çalıştırılırken, `readonly` alanların serileştirme `public` ve `private`deserialization (hem de) desteklenmez. Bunun nedeni, oluşturulan IL'nin doğrulanamayan olması ve bu nedenle yüksek izinler gerektirmesidir.

- Hem <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> kısmi bir güven ortamında desteklenir. Ancak, kullanımı <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki koşullara tabidir:

  - Tüm serileştirilebilir `[DataContract]` türleri ortak olmalıdır.

  - Bir `[DataContract]` türdeki `[DataMember]` tüm serileştirilebilir alanlar veya özellikler herkese açık olmalı ve okuma/yazma olmalıdır. Kısmen güvenilen `readonly` bir uygulamada WCF çalıştırılırken alanların serileştirme ve deserialization desteklenmez.

  - `[Serializable]` / Programlama `ISerializable]` modeli kısmi bir güven ortamında desteklenmez.

  - Bilinen türler kod veya makine düzeyinde yapılandırmada belirtilmelidir (`Machine.config`). Bilinen türler, güvenlik nedenleriyle uygulama düzeyinde yapılandırmada belirtilemez.

- Yöntem güvenlik izni `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`gerektirdiğinden, kısmen güvenilen bir ortama özel durum atan türler. <xref:System.Runtime.Serialization.IObjectReference> <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A>

## <a name="additional-notes-on-serialization"></a>Serileştirme İlave Notlar

Aşağıdaki kurallar, Veri Sözleşmesi Serializer tarafından desteklenen türler için de geçerlidir:

- Genel türleri tamamen veri sözleşmesi serializer tarafından desteklenir.

- Nullable değer türleri tamamen veri sözleşmesi serializer tarafından desteklenir.

- Arabirim türleri, <xref:System.Object> koleksiyon arabirimleri söz konusu olduğunda, koleksiyon türleri olarak kabul edilir.

- Hem yapılar hem de sınıflar desteklenir.

- Web <xref:System.Runtime.Serialization.DataContractSerializer> hizmetleri ve ASP.NET tarafından kullanılan <xref:System.Xml.Serialization.XmlSerializer> programlama modelini desteklemez. Özellikle, gibi <xref:System.Xml.Serialization.XmlElementAttribute> öznitelikleri desteklemez <xref:System.Xml.Serialization.XmlAttributeAttribute>ve . Bu programlama modeli için destek etkinleştirmek için, WCF <xref:System.Xml.Serialization.XmlSerializer> yerine <xref:System.Runtime.Serialization.DataContractSerializer>kullanmak için anahtarlanmış olmalıdır.

- Türü <xref:System.DBNull> özel bir şekilde tedavi edilir. Bu bir singleton türüdür ve deserializer deserializer singleton kısıtlamasaygı `DBNull` ve singleton örneğine tüm referansları puan. Serileştirilebilir `DBNull` bir tür olduğundan, <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> izin ister.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Anlaşmalarında XML ve ADO.NET Türleri](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)
- [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Seri Hale Getirilebilir Türler](../../../../docs/framework/wcf/feature-details/serializable-types.md)
- [Veri Anlaşmalarında Koleksiyon Türleri](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)
- [Veri Sözleşmelerinde Numaralandırma Türleri](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)
