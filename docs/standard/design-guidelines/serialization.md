---
title: Serileştirme
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
ms.openlocfilehash: d07549da371e403adca089c601ee5b028b268086
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291688"
---
# <a name="serialization"></a>Serileştirme
Serileştirme, bir nesneyi, kolayca kalıcı veya taşınan bir biçime dönüştürme işlemidir. Örneğin, bir nesneyi seri hale getirebilirsiniz, HTTP kullanarak Internet üzerinden taşıyabilirsiniz ve hedef makinede serisi kaldırılamaz.

 .NET Framework, çeşitli serileştirme senaryoları için optimize edilmiş üç ana serileştirme teknolojisi sunar. Aşağıdaki tablo, bu teknolojiler ve bu teknolojiler için ilgili ana Framework türleri listeler.

|**Teknoloji adı**|**Ana türler**|**Senaryolar**|
|-------------------------|--------------------|-------------------|
|**Veri sözleşmesi serileştirme**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Genel kalıcılığı<br />Web Hizmetleri<br />JSON|
|**XML serileştirme**|<xref:System.Xml.Serialization.XmlSerializer>|XML şekli üzerinde tam denetim içeren XML biçimi|
|**Çalışma zamanı serileştirme (Ikili ve SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET uzaktan iletişim|

 ✔️, yeni türler tasarlarken serileştirme hakkında düşünün.

## <a name="choosing-the-right-serialization-technology-to-support"></a>Destek için sağ serileştirme teknolojiyi seçmenizde
 ✔️, Web hizmetlerinde kalıcı veya kullanımda olması gerekiyorsa, veri sözleşmesi serileştirmesini desteklemeyi düşünün.

 ✔️, bir tür serileştirildiğinde üretilen XML biçimi üzerinde daha fazla denetime ihtiyacınız varsa veri anlaşması serileştirmesine ek olarak veya veri sözleşmesi serileştirmesi yerine XML serileştirmesini desteklemeyi düşünün.

 Bu, veri sözleşme serileştirmesi tarafından desteklenmeyen bir XML yapısı kullanmanız gereken (örneğin, XML özniteliklerini üretmek için), birlikte çalışabilirlik senaryolarında gerekli olabilir.

 ✔️, .NET uzaktan Iletişim sınırları arasında seyahat etmeniz gerekiyorsa, çalışma zamanı serileştirmesini desteklemeyi düşünün.

 ❌Yalnızca genel Kalıcılık nedenleriyle çalışma zamanı serileştirme veya XML serileştirme desteği kullanmaktan kaçının. Bunun yerine veri sözleşmesi serileştirmesini tercih edin.

## <a name="supporting-data-contract-serialization"></a>Veri sözleşmesi serileştirmesini destekleme
 Türler, türü <xref:System.Runtime.Serialization.DataContractAttribute> için ve <xref:System.Runtime.Serialization.DataMemberAttribute> türüne (alanları ve Özellikler) türüne uygulayarak veri sözleşmesi serileştirmesini destekleyebilir.

 ✔️, türün kısmi güvende kullanılabilmesi için, genel türünden veri üyelerini işaretlemeyi düşünün.

 Tam güvende, veri sözleşme serileştiricileri ortak türleri ve üyeleri seri hale getirilebilir ve serisini kaldıramıyor, ancak kısmi güvende yalnızca ortak üyeler seri hale getirilebilir ve seri durumdan çıkarılamaz.

 ✔️, sahip olan tüm özelliklerde bir alıcı ve ayarlayıcı uygular <xref:System.Runtime.Serialization.DataMemberAttribute> . Veri sözleşme serileştiricileri, tür için hem alıcının hem de ayarlayıcının seri hale getirilebilir olarak kabul edilmesini gerektirir. (.NET Framework 3,5 SP1'DE, bazı koleksiyon özellikleri salt alınabilir.) Tür kısmi güvende kullanılmazsa, özellik erişimcilerinin biri veya her ikisi ortak olabilir.

 ✔️ Serisi kaldırılan örneklerin başlatılması için serileştirme geri çağırmaları kullanmayı düşünün.

 Nesneler seri durumdan kaldırıldığında oluşturucular çağrılmaz. (Kural için özel durumlar vardır. İle işaretlenmiş koleksiyonların oluşturucuları <xref:System.Runtime.Serialization.CollectionDataContractAttribute> seri durumundan çıkarma sırasında çağırılır.) Bu nedenle, normal oluşturma sırasında yürütülen tüm mantığın serileştirme geri çağırmalarından biri olarak uygulanması gerekir.

 `OnDeserializedAttribute`en yaygın olarak kullanılan geri çağırma özniteliğidir. Ailesindeki diğer öznitelikler, ve ' dir <xref:System.Runtime.Serialization.OnDeserializingAttribute> <xref:System.Runtime.Serialization.OnSerializingAttribute> <xref:System.Runtime.Serialization.OnSerializedAttribute> . Seri durumundan çıkarma, serileştirme önce ve son olarak seri hale getirme sonra önce sırasıyla yürütülen geri çağırmaları işaretlemek için kullanılabilir.

 ✔️, <xref:System.Runtime.Serialization.KnownTypeAttribute> karmaşık bir nesne grafiğinin serisini kaldırmada kullanılması gereken somut türleri göstermek için öğesini KULLANMAYı düşünün.

 ✔️, seri hale getirilebilir türler oluştururken veya değiştirirken geri ve ileri uyumluluklarını göz önünde bulundurun.

 Bu türden gelecek sürümlerin serileştirilmiş akışlarının, türün geçerli sürümüne seri durumdan çıkarılabileceğini ve bunun tersini aklınızda bulundurun.

 Veri sözleşmesi özniteliklerine açık parametreler kullanarak sözleşmeyi korumak için özel bir işlem yapılmadığı takdirde, hatta özel ve dahili olan veri üyelerinin, ad, tür veya hatta sıralarını bu tür bir şekilde değiştiremediğiniz emin olun.

 Seri hale getirilebilir türlerde değişiklik yaparken serileştirme test uyumluluğu. Yeni sürümü eski bir sürüme serisini çıkarmayı deneyin, tersi de geçerlidir.

 ✔️ <xref:System.Runtime.Serialization.IExtensibleDataObject> , türün farklı sürümleri arasında gidiş dönüşü sağlamak için uygulamayı düşünün.

 Arabirim, seri hale getiricinin, gidiş dönüşü sırasında hiçbir veri kaybolmamasını sağlar. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType>Özelliği, geçerli sürüme bilinmeyen türün gelecekteki sürümünden verileri depolamak için kullanılır ve bu nedenle veri üyelerinde depolayamez. Geçerli sürüm daha sonra serileştirilildiğinde ve gelecek bir sürüme seri durumdan çıkarılacağından, ek veriler serileştirilmiş akışta kullanılabilir.

## <a name="supporting-xml-serialization"></a>XML serileştirme destekleme
 Veri anlaşması serileştirme .NET Framework, ancak veri sözleşmesi serileştirmesi tarafından desteklenmeyen serileştirme senaryoları vardır. Örneğin, seri hale getirici tarafından üretilen veya tüketilen XML şekli üzerinde size tam denetim vermez. Bu tür hassas denetim gerekliyse, XML serileştirmesi kullanılmalıdır ve bu serileştirme teknolojisini desteklemek için türlerinizi tasarlamanız gerekir.

 ❌Oluşturulan XML şeklini denetlemek için çok güçlü bir nedeniniz yoksa, özel olarak XML serileştirme için türlerinizi tasarlamaktan KAÇıNıN. Bu serileştirme teknolojisinin yerini, önceki bölümde ele alınan veri sözleşmesi serileştirmesi almıştır.

 ✔️ <xref:System.Xml.Serialization.IXmlSerializable> , XML serileştirme öznitelikleri uygulanarak, seri hale GETIRILEN XML şekli üzerinde daha fazla denetime sahip olmak istiyorsanız arabirimi uygulamayı düşünün. Arabiriminin iki yöntemi <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> ve <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> , serileştirilmiş XML akışını tam olarak denetlemenize olanak tanır. Ayrıca, uygulanarak, türü için oluşturulan XML şemasını da denetleyebilirsiniz `XmlSchemaProviderAttribute` .

## <a name="supporting-runtime-serialization"></a>Çalışma zamanı serileştirme destekleme
 Çalışma zamanı serileştirme .NET uzaktan Iletişim tarafından kullanılan bir teknolojidir. Türlerinizi .NET uzaktan Iletişim kullanılarak aktarılyacağını düşünüyorsanız, çalışma zamanı serileştirmesini desteklediklerinden emin olmanız gerekir.

 Çalışma zamanı serileştirme için temel destek,, <xref:System.SerializableAttribute> ve daha gelişmiş senaryolar, basit bir çalışma zamanı seri hale getirilebilir bir model (uygulama <xref:System.Runtime.Serialization.ISerializable> ve sağlama serileştirme Oluşturucusu) uygulanmasını içerir.

 ✔️, .NET uzaktan Iletişim ile türlerinizi kullanılacaksa, çalışma zamanı serileştirmesini desteklemeyi düşünün. Örneğin, <xref:System.AddIn?displayProperty=nameWithType> ad alanı .NET uzaktan iletişimini kullanır ve bu nedenle eklentiler arasında değiş tokuş edilen tüm türlerin `System.AddIn` çalışma zamanı serileştirmesini desteklemesi gerekir.

 serileştirme işlemi üzerinde komple denetim istiyorsanız, çalışma zamanı serileştirilebilir modelini uygulamayı ✔️. Örneğin, verileri serileştirilmiş veya seri durumdan çıkarılan şekilde dönüştürmek istiyorsanız.

 Düzen çok basit yöneliktir. Yapmanız gereken tek şey, <xref:System.Runtime.Serialization.ISerializable> arabirimini uygular ve nesne seri durumdan çıkarıldığınızda kullanılan özel bir Oluşturucu sağlamaktır.

 ✔️ serileştirme oluşturucuyu korumalı hale getirir ve burada örnekte gösterildiği gibi tam olarak adlandırılan ve adlandırılmış iki parametre sağlar.

```csharp
[Serializable]
public class Person : ISerializable
{
    protected Person(SerializationInfo info, StreamingContext context)
    {
        // ...
    }
}
```

 üyeleri açıkça uygulama ✔️ <xref:System.Runtime.Serialization.ISerializable> .

 ✔️, uygulamaya bir bağlantı talebi uygular <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> . Bu, yalnızca tam olarak güvenilen çekirdek ve çalışma zamanı serileştirici üyeye erişimine sahip olmasını sağlar.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Kullanım yönergeleri](usage-guidelines.md)
