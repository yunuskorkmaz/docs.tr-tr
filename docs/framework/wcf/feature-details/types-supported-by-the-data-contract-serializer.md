---
title: Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler
description: WCF veri sözleşmesinin serileştirici serileştirme ve seri durumdan çıkarma için desteklediği türlerin tüm listesine bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: ef9d2e61ab7121c97bd474bb151fee32907b1dac
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246538"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler

Windows Communication Foundation (WCF), <xref:System.Runtime.Serialization.DataContractSerializer> VERILERI XML 'e dönüştürmek ve XML 'i yeniden verilere dönüştürmek için varsayılan serileştirme altyapısını kullanır. , <xref:System.Runtime.Serialization.DataContractSerializer> *Veri anlaşması* türlerini seri hale getirmek için tasarlanmıştır. Ancak, örtük bir veri sözleşmesine sahip olma gibi düşünülebilir, diğer birçok türü destekler. Aşağıda, seri hale getirilebilen türlerin kapsamlı bir listesi verilmiştir:

- Parametreleri olmayan bir oluşturucuya sahip olan tüm herkese açık görünen türler.

- Veri anlaşması türleri. Bunlar, özniteliğin uygulandığı türlerdir <xref:System.Runtime.Serialization.DataContractAttribute> . İş nesnelerini temsil eden yeni özel türler normalde veri sözleşmesi türleri olarak oluşturulmalıdır. Daha fazla bilgi için bkz. [veri sözleşmeleri](using-data-contracts.md) ve [serileştirilebilir türler](serializable-types.md)kullanma.

- Koleksiyon türleri. Bunlar, veri listelerini temsil eden türlerdir. Bunlar, ve gibi koleksiyon türleri veya gibi düzenli diziler olabilir <xref:System.Collections.ArrayList> <xref:System.Collections.Generic.Dictionary%602> . <xref:System.Runtime.Serialization.CollectionDataContractAttribute>Özniteliği bu türlerin serileştirmesini özelleştirmek için kullanılabilir, ancak gerekli değildir. Daha fazla bilgi için bkz. [veri sözleşmeleri Içindeki koleksiyon türleri](collection-types-in-data-contracts.md).

- Sabit listesi türleri. Bayrak numaralandırmaları dahil olmak üzere numaralandırmalar seri hale getirilebilir. İsteğe bağlı olarak, numaralandırma türleri <xref:System.Runtime.Serialization.DataContractAttribute> özniteliğiyle işaretlenebilir, bu durumda serileştirme 'e katılan her üyenin özniteliğiyle işaretlenmesi gerekir <xref:System.Runtime.Serialization.EnumMemberAttribute> . İşaretlenmeyen Üyeler serileştirilmez. Daha fazla bilgi için bkz. [veri sözleşmeleri Içindeki numaralandırma türleri](enumeration-types-in-data-contracts.md).

- İlkel türler .NET Framework. .NET Framework yerleşik olarak bulunan aşağıdaki türlerin hepsi seri hale getirilebilir ve temel türler olarak kabul edilir: <xref:System.Byte> ,,, <xref:System.SByte> <xref:System.Int16> <xref:System.Int32> , <xref:System.Int64> , <xref:System.UInt16> , <xref:System.UInt32> , <xref:System.UInt64> , <xref:System.Single> , <xref:System.Double> , <xref:System.Boolean> , <xref:System.Char> , <xref:System.Decimal> , <xref:System.Object> , ve <xref:System.String> .

- Diğer temel türler. Bu türler .NET Framework temel değildir, ancak serileştirilmiş XML biçiminde temel öğeler olarak değerlendirilir. Bu türler,,,,, <xref:System.DateTime> <xref:System.DateTimeOffset> <xref:System.TimeSpan> <xref:System.Guid> <xref:System.Uri> <xref:System.Xml.XmlQualifiedName> ve dizilerdir <xref:System.Byte> .

  > [!NOTE]
  > Diğer temel türlerin aksine, <xref:System.DateTimeOffset> Varsayılan olarak bilinen bir tür değildir. Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](data-contract-known-types.md)).

- Özniteliği ile işaretlenmiş türler <xref:System.SerializableAttribute> . .NET Framework temel sınıf kitaplığına dahil edilen birçok tür bu kategoriye girer. , <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Arabirimi için destek de dahil olmak üzere .NET Framework uzaktan iletişim,, ve tarafından kullanılan bu serileştirme programlama modelini tam olarak destekler <xref:System.Runtime.Serialization.ISerializable> .

- Ham XML veya ADO.NET ilişkisel verileri temsil eden türleri temsil eden türler. <xref:System.Xml.XmlElement>Ve türleri dizisi, <xref:System.Xml.XmlNode> XML 'i doğrudan temsil etmenin bir yolu olarak desteklenir. Ayrıca, arayüzü uygulayan türler <xref:System.Xml.Serialization.IXmlSerializable> , ilgili <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliği ve <xref:System.Xml.Linq.XDocument> ve türleri de dahil olmak üzere desteklenir <xref:System.Xml.Linq.XElement> . ADO.NET <xref:System.Data.DataTable> türünün ve <xref:System.Data.DataSet> türünün (Ayrıca, türü belirtilmiş türetilmiş sınıfları) tüm <xref:System.Xml.Serialization.IXmlSerializable> arabirimini uygular ve bu nedenle bu kategoriye uygun. Daha fazla bilgi için bkz. [veri sözleşmeleri Içindeki XML ve ADO.net türleri](xml-and-ado-net-types-in-data-contracts.md).

## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Kısmi güven modunda belirli türleri kullanma sınırlamaları

Aşağıda, kısmi güven modu senaryolarında belirli türleri kullanırken kısıtlamaların bir listesi verilmiştir:

- Kullanılarak kısmen güvenilen kodda uygulayan bir türü seri hale getirmek veya serisini kaldırmak için <xref:System.Runtime.Serialization.ISerializable> <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> ve <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> izinlerini gerektirir.

- WCF kodunu [kısmi güven](partial-trust.md) modunda çalıştırırken, alanların serileştirilmesi ve seri durumundan çıkarılması `readonly` (hem hem `public` de `private` ) desteklenmez. Bunun nedeni, üretilen IL 'nin doğrulanamaz olması ve bu nedenle yükseltilmiş izinler gerektirmesidir.

- Hem hem de <xref:System.Runtime.Serialization.DataContractSerializer> , <xref:System.Xml.Serialization.XmlSerializer> kısmi güven ortamında desteklenir. Ancak, öğesinin kullanımı <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki koşullara tabidir:

  - Tüm serileştirilebilir `[DataContract]` türler ortak olmalıdır.

  - Bir türdeki tüm seri hale getirilebilir `[DataMember]` alanların veya özelliklerin `[DataContract]` ortak ve okuma/yazma olması gerekir. `readonly`Bir kısmen güvenilen uygulamada WCF çalıştırılırken alanların serileştirilmesi ve seri durumundan çıkarılması desteklenmez.

  - `[Serializable]` / `ISerializable]` Programlama modeli kısmi güven ortamında desteklenmez.

  - Bilinen türler kod veya makine düzeyinde yapılandırma () içinde belirtilmelidir `Machine.config` . Bilinen türler güvenlik nedeniyle uygulama düzeyi yapılandırmasında belirtilemez.

- Uygulayan türler <xref:System.Runtime.Serialization.IObjectReference> , güvenlik izni gerektirdiğinden, kısmen güvenilen bir ortamda özel durum oluşturur <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]` .

## <a name="additional-notes-on-serialization"></a>Serileştirme ile ilgili ek notlar

Aşağıdaki kurallar, veri sözleşmesi seri hale getirici tarafından desteklenen türler için de geçerlidir:

- Genel türler, veri sözleşmesi serileştiricisi tarafından tamamen desteklenir.

- Null yapılabilir değer türleri, veri sözleşmesi serileştiricisi tarafından tamamen desteklenir.

- Arabirim türleri, koleksiyon <xref:System.Object> türleri olarak koleksiyon arabirimleri olması durumunda ya da olarak değerlendirilir.

- Her iki yapı ve sınıf de desteklenir.

- , <xref:System.Runtime.Serialization.DataContractSerializer> Ve ASP.NET Web Hizmetleri tarafından kullanılan programlama modelini desteklemez <xref:System.Xml.Serialization.XmlSerializer> . Özellikle, ve gibi öznitelikleri desteklemez <xref:System.Xml.Serialization.XmlElementAttribute> <xref:System.Xml.Serialization.XmlAttributeAttribute> . Bu programlama modeli desteğini etkinleştirmek için WCF 'nin yerine kullanmak üzere geçiş yapılmalıdır <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> .

- <xref:System.DBNull>Tür özel bir şekilde ele alınır. Tek bir türdür ve seri hale getiricinin serisini kaldırma işlemi, Singleton kısıtlamasına uyar ve `DBNull` tek örneğe tüm başvuruları gösterir. `DBNull`Seri hale getirilebilir bir tür olduğundan, izin talep edilir <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> .

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Anlaşmalarında XML ve ADO.NET Türleri](xml-and-ado-net-types-in-data-contracts.md)
- [Veri Anlaşmalarını Kullanma](using-data-contracts.md)
- [Seri Hale Getirilebilir Türler](serializable-types.md)
- [Veri Anlaşmalarında Koleksiyon Türleri](collection-types-in-data-contracts.md)
- [Veri Sözleşmelerinde Numaralandırma Türleri](enumeration-types-in-data-contracts.md)
