---
title: Serileştirme
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
ms.openlocfilehash: fb5d714e2452f1b9c1dcc79cc179b35a2dd48fec
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709081"
---
# <a name="serialization"></a>Serileştirme
Serileştirme, bir nesneyi, kolayca kalıcı veya taşınan bir biçime dönüştürme işlemidir. Örneğin, bir nesneyi seri hale getirebilirsiniz, HTTP kullanarak Internet üzerinden taşıyabilirsiniz ve hedef makinede serisi kaldırılamaz.  
  
 .NET Framework, çeşitli serileştirme senaryoları için optimize edilmiş üç ana serileştirme teknolojisi sunar. Aşağıdaki tablo, bu teknolojiler ve bu teknolojiler için ilgili ana Framework türleri listeler.  
  
|**Teknoloji adı**|**Ana türler**|**Senaryolar**|  
|-------------------------|--------------------|-------------------|  
|**Veri sözleşmesi serileştirme**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Genel kalıcılığı<br />Web Hizmetleri<br />JSON|  
|**XML serileştirme**|<xref:System.Xml.Serialization.XmlSerializer>|XML şekli üzerinde tam denetim içeren XML biçimi|  
|**Çalışma zamanı serileştirme (Ikili ve SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET uzaktan iletişim|  
  
 **✓ DO** yeni türleri tasarlarken serileştirme düşünün.  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>Destek için sağ serileştirme teknolojiyi seçmenizde  
 **✓ CONSIDER** türünüz örneklerini kalıcı veya Web Hizmetleri içinde kullanılan gerekebilir, veri sözleşmesi seri hale getirme destekleme.  
  
 **✓ CONSIDER** türü serileştirildiğinde üreten XML biçimi hakkında daha fazla denetime ihtiyacınız varsa XML serileştirme yerine veya veri sözleşmesi seri hale getirme ek destek.  
  
 Bu, veri sözleşme serileştirmesi tarafından desteklenmeyen bir XML yapısı kullanmanız gereken (örneğin, XML özniteliklerini üretmek için), birlikte çalışabilirlik senaryolarında gerekli olabilir.  
  
 **✓ CONSIDER** türünüz örnekleri .NET uzaktan iletişim sınırlarında seyahat gerekiyorsa çalışma zamanı serileştirme destekleme.  
  
 **X AVOID** çalışma zamanı serileştirme veya XML serileştirme yalnızca genel Kalıcılık nedenlerle destekleme. Bunun yerine veri sözleşmesi serileştirmesini tercih edin.  
  
## <a name="supporting-data-contract-serialization"></a>Veri sözleşmesi serileştirmesini destekleme  
 Türler, türü <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> üyelere (alanlar ve Özellikler) uygulayarak veri sözleşmesi serileştirmesini destekleyebilir.  
  
 **✓ CONSIDER** türü kısmi güvende kullanılabiliyorsa, genel türde veri üyeleri işaretleme.  
  
 Tam güvende, veri sözleşme serileştiricileri ortak türleri ve üyeleri seri hale getirilebilir ve serisini kaldıramıyor, ancak kısmi güvende yalnızca ortak üyeler seri hale getirilebilir ve seri durumdan çıkarılamaz.  
  
 **✓ DO** bir alıcı ve ayarlayıcıya sahip tüm özellikleri uygulamak <xref:System.Runtime.Serialization.DataMemberAttribute>. Veri sözleşme serileştiricileri, tür için hem alıcının hem de ayarlayıcının seri hale getirilebilir olarak kabul edilmesini gerektirir. (.NET Framework 3,5 SP1'DE, bazı koleksiyon özellikleri salt alınabilir.) Tür kısmi güvende kullanılmazsa, özellik erişimcilerinin biri veya her ikisi ortak olabilir.  
  
 **✓ CONSIDER** seri durumdan çıkarılmış örneklerinin başlatma için seri hale getirme geri çağrıları kullanarak.  
  
 Nesneler seri durumdan kaldırıldığında oluşturucular çağrılmaz. (Kural için özel durumlar vardır. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> ile işaretlenmiş koleksiyonların oluşturucuları seri durumundan çıkarma sırasında çağrılır.) Bu nedenle, normal oluşturma sırasında yürütülen tüm mantığın serileştirme geri çağırmalarından biri olarak uygulanması gerekir.  
  
 `OnDeserializedAttribute` en yaygın olarak kullanılan geri çağırma özniteliğidir. Ailedeki diğer öznitelikler <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute>ve <xref:System.Runtime.Serialization.OnSerializedAttribute>. Seri durumundan çıkarma, serileştirme önce ve son olarak seri hale getirme sonra önce sırasıyla yürütülen geri çağırmaları işaretlemek için kullanılabilir.  
  
 **✓ CONSIDER** kullanarak <xref:System.Runtime.Serialization.KnownTypeAttribute> karmaşık nesne grafiğinin seri durumdan çıkarılırken kullanılmalıdır somut türleri belirtmek için.  
  
 **✓ DO** oluştururken veya seri hale getirilebilir türler değiştirme ileriye ve geriye dönük uyumluluk göz önünde bulundurun.  
  
 Bu türden gelecek sürümlerin serileştirilmiş akışlarının, türün geçerli sürümüne seri durumdan çıkarılabileceğini ve bunun tersini aklınızda bulundurun.  
  
 Veri sözleşmesi özniteliklerine açık parametreler kullanarak sözleşmeyi korumak için özel bir işlem yapılmadığı takdirde, hatta özel ve dahili olan veri üyelerinin, ad, tür ve hatta sıralarını bu türün gelecekteki sürümlerinde değiştiremediğinize emin olun. .  
  
 Seri hale getirilebilir türlerde değişiklik yaparken serileştirme test uyumluluğu. Yeni sürümü eski bir sürüme serisini çıkarmayı deneyin, tersi de geçerlidir.  
  
 **✓ CONSIDER** uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> türü farklı sürümleri arasında gidiş izin vermek için.  
  
 Arabirim, seri hale getiricinin, gidiş dönüşü sırasında hiçbir veri kaybolmamasını sağlar. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> özelliği, geçerli sürüme bilinmeyen bir türün gelecekteki sürümünden verileri depolamak için kullanılır ve bu nedenle veri üyelerinde depolayamez. Geçerli sürüm daha sonra serileştirilildiğinde ve gelecek bir sürüme seri durumdan çıkarılacağından, ek veriler serileştirilmiş akışta kullanılabilir.  
  
## <a name="supporting-xml-serialization"></a>XML serileştirme destekleme  
 Veri anlaşması serileştirme .NET Framework, ancak veri sözleşmesi serileştirmesi tarafından desteklenmeyen serileştirme senaryoları vardır. Örneğin, seri hale getirici tarafından üretilen veya tüketilen XML şekli üzerinde size tam denetim vermez. Bu tür hassas denetim gerekliyse, XML serileştirmesi kullanılmalıdır ve bu serileştirme teknolojisini desteklemek için türlerinizi tasarlamanız gerekir.  
  
 **X AVOID** XML şeklini denetlemek için çok güçlü bir nedeniniz yoksa, türlerinizi XML serileştirmesi için özellikle tasarlama üretilen. Bu serileştirme teknolojisinin yerini, önceki bölümde ele alınan veri sözleşmesi serileştirmesi almıştır.  
  
 **✓ CONSIDER** uygulama <xref:System.Xml.Serialization.IXmlSerializable> ne XML serileştirme özniteliklerini uygulayarak sunulan daha serileştirilmiş XML şekli üzerinde daha fazla denetim isterseniz, arabirim. <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> ve <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>arabirimin iki yöntemi, serileştirilmiş XML akışını tam olarak denetlemenize olanak tanır. Ayrıca, `XmlSchemaProviderAttribute`uygulanarak, tür için oluşturulan XML şemasını da denetleyebilirsiniz.  
  
## <a name="supporting-runtime-serialization"></a>Çalışma zamanı serileştirme destekleme  
 Çalışma zamanı serileştirme .NET uzaktan Iletişim tarafından kullanılan bir teknolojidir. Türlerinizi .NET uzaktan Iletişim kullanılarak aktarılyacağını düşünüyorsanız, çalışma zamanı serileştirmesini desteklediklerinden emin olmanız gerekir.  
  
 Çalışma zamanı serileştirme için temel destek <xref:System.SerializableAttribute>uygulanarak sağlanır ve daha gelişmiş senaryolar basit bir çalışma zamanı seri hale getirilebilir bir model (<xref:System.Runtime.Serialization.ISerializable> uygulayın ve serileştirme Oluşturucusu sağlar) uygulamayı içerir.  
  
 **✓ CONSIDER** türlerinizi .NET uzaktan iletişim ile kullanılacaksa, çalışma zamanı serileştirme destekleme. Örneğin, <xref:System.AddIn?displayProperty=nameWithType> ad alanı .NET uzaktan iletişimini kullanır ve bu nedenle `System.AddIn` eklentileri arasında değiş tokuş edilen tüm türlerin çalışma zamanı serileştirmesini desteklemesi gerekir.  
  
 **✓ CONSIDER** seri hale getirme işlemi üzerinde tam denetimi istiyorsanız çalışma zamanı seri hale getirilebilir düzeni uygulama. Örneğin, verileri serileştirilmiş veya seri durumdan çıkarılan şekilde dönüştürmek istiyorsanız.  
  
 Düzen çok basit yöneliktir. Yapmanız gereken tek şey <xref:System.Runtime.Serialization.ISerializable> arabirimini uygular ve nesne seri durumdan çıkarıldığınızda kullanılan özel bir oluşturucu sağlar.  
  
 **✓ DO** korumalı serileştirme Oluşturucusu oluşturarak yazılan ve tam olarak burada aşağıdaki örnekte gösterildiği gibi adlı iki parametre sağlayabilirsiniz.  
  
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
  
 **✓ DO** uygulamak <xref:System.Runtime.Serialization.ISerializable> üyeleri açıkça.  
  
 **✓ DO** bir bağlantı isteği uygulamak <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> uygulaması. Bu, yalnızca tam olarak güvenilen çekirdek ve çalışma zamanı serileştirici üyeye erişimine sahip olmasını sağlar.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
