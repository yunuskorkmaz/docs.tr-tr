---
title: Serialization1
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
author: KrzysztofCwalina
ms.openlocfilehash: f0ef8ab378fb3898f2d2e134f0b38668f6794ef3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650160"
---
# <a name="serialization"></a>Serileştirme
Serileştirme bir nesneyi kolayca kalıcı yapılabilecek veya taşınabilecek bir biçime dönüştürme işlemidir. Örneğin, bir nesneyi serileştirmek, HTTP kullanarak ve hedef makinenin serisi Internet üzerinden aktarım.  
  
 .NET Framework çeşitli serileştirme senaryolar için en iyi duruma getirilmiş üç ana serileştirme teknolojiler sunar. Aşağıdaki tablo, bu teknolojiler ve bu teknolojiler için ilgili ana Framework türleri listeler.  
  
|**Teknoloji adı**|**Ana türü**|**Senaryoları**|  
|-------------------------|--------------------|-------------------|  
|**Veri sözleşme seri hale getirme**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Genel kalıcılığı<br />Web Hizmetleri<br />JSON|  
|**XML serileştirme**|<xref:System.Xml.Serialization.XmlSerializer>|XML biçimi XML şekli üzerinde tam denetim|  
|**Çalışma zamanı serileştirme (ikili ve SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET uzaktan iletişim|  
  
 **✓ DO** yeni türleri tasarlarken serileştirme düşünün.  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>Destek için sağ serileştirme teknolojiyi seçmenizde  
 **✓ CONSIDER** türünüz örneklerini kalıcı veya Web Hizmetleri içinde kullanılan gerekebilir, veri sözleşmesi seri hale getirme destekleme.  
  
 **✓ CONSIDER** türü serileştirildiğinde üreten XML biçimi hakkında daha fazla denetime ihtiyacınız varsa XML serileştirme yerine veya veri sözleşmesi seri hale getirme ek destek.  
  
 Bu, veri sözleşme seri hale getirme tarafından Örneğin, XML özniteliği üretmek için desteklenmeyen bir XML kullanmak için gerek duyduğunuz senaryoları oluşturmak bazı birlikte çalışabilirlik gerekli olabilir.  
  
 **✓ CONSIDER** türünüz örnekleri .NET uzaktan iletişim sınırlarında seyahat gerekiyorsa çalışma zamanı serileştirme destekleme.  
  
 **X AVOID** çalışma zamanı serileştirme veya XML serileştirme yalnızca genel Kalıcılık nedenlerle destekleme. Bunun yerine veri sözleşme serileştirme tercih.  
  
## <a name="supporting-data-contract-serialization"></a>Destek veri sözleşme seri hale getirme  
 Türleri uygulayarak veri sözleşme serileştirme destekleyebilir <xref:System.Runtime.Serialization.DataContractAttribute> türüne ve <xref:System.Runtime.Serialization.DataMemberAttribute> üyelerine (alanlar ve Özellikler) türü.  
  
 **✓ CONSIDER** türü kısmi güvende kullanılabiliyorsa, genel türde veri üyeleri işaretleme.  
  
 Tam güven veri sözleşme serileştiricileri seri hale getirmek ve özel tür ve üyelerinin seri durumdan, ancak yalnızca ortak üyeleri sıralanabilir ve kısmi güvende seri durumdan.  
  
 **✓ DO** bir alıcı ve ayarlayıcıya sahip tüm özellikleri uygulamak <xref:System.Runtime.Serialization.DataMemberAttribute>. Veri sözleşme serileştiricileri alıcı hem seri hale getirilebilir değerlendirilmesi türünün ayarlama gerektirir. (.NET Framework 3.5 SP1'de, bazı koleksiyon özellikleri salt alma olabilir.) Kısmi güven türü kullanılmaz, bir veya iki özellik erişimcisi özel olabilir.  
  
 **✓ CONSIDER** seri durumdan çıkarılmış örneklerinin başlatma için seri hale getirme geri çağrıları kullanarak.  
  
 Nesneleri seri zaman oluşturucular çağrılır değil. (Bu kuralın istisnası vardır. Koleksiyonların oluşturucular ile işaretlenen <xref:System.Runtime.Serialization.CollectionDataContractAttribute> seri durumundan çıkarma sırasında çağrılır.) Bu nedenle, normal yapım sırasında yürüten herhangi bir mantık serileştirme geri çağırmaları biri olarak uygulanması gerekiyor.  
  
 `OnDeserializedAttribute` en yaygın kullanılan geri çağırma özniteliğidir. Diğer öznitelikler ailesindeki <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute>, ve <xref:System.Runtime.Serialization.OnSerializedAttribute>. Seri durumundan çıkarma, serileştirme önce ve son olarak seri hale getirme sonra önce sırasıyla yürütülen geri çağırmaları işaretlemek için kullanılabilir.  
  
 **✓ CONSIDER** kullanarak <xref:System.Runtime.Serialization.KnownTypeAttribute> karmaşık nesne grafiğinin seri durumdan çıkarılırken kullanılmalıdır somut türleri belirtmek için.  
  
 **✓ DO** oluştururken veya seri hale getirilebilir türler değiştirme ileriye ve geriye dönük uyumluluk göz önünde bulundurun.  
  
 Akış türünüz sonraki sürümlerinde serileştirilmiş unutmayın türü geçerli sürüme seri ve tersi.  
  
 Özel veri sözleşme öznitelikleri için açık parametrelerini kullanarak sözleşme korumak için açıklanmamasına sürece veri üyeleri, hatta özel ve dahili, adları, türleri veya hatta sıralamalarını türü gelecekteki sürümlerinde değiştiremezsiniz anlamak emin olun .  
  
 Serileştirme uyumluluk serializable türler için değişiklik yaparken test edin. Yeni sürümü eski bir sürüme serisi kaldırılırken deneyin ve tersi.  
  
 **✓ CONSIDER** uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> türü farklı sürümleri arasında gidiş izin vermek için.  
  
 Seri hale getirici gidiş dönüşü sırasında hiçbir veri kaybı olduğundan emin olmak arabirim sağlar. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> Özelliği, geçerli sürümü için bilinmeyen tür, gelecekteki sürümüne tüm verileri depolamak için kullanılır ve bu nedenle, depolayamaz, veri üyeleri. Geçerli sürüm daha sonra serileştirilmiş ve gelecekteki bir sürümüne seri durumdan, ek verileri seri hale getirilmiş stream'de kullanıma sunulacaktır.  
  
## <a name="supporting-xml-serialization"></a>XML serileştirme destekleme  
 Veri sözleşme seri hale getirme (varsayılan) ana olan serileştirme teknoloji .NET Framework, ancak veri sözleşme serileştirme desteklemediği serileştirme senaryolar vardır. Örneğin, bu, üretilen veya serileştiricisi tarafından kullanılan XML şekli üzerinde tam denetim vermez. Bu tür iyi denetim gerekliyse, XML serileştirme kullanılacak olan ve bu serileştirme teknoloji desteklemek için türleri tasarlamak için ihtiyacınız.  
  
 **X AVOID** XML şeklini denetlemek için çok güçlü bir nedeniniz yoksa, türlerinizi XML serileştirmesi için özellikle tasarlama üretilen. Bu seri hale getirme teknoloji önceki bölümde açıklanan veri sözleşme serileştirme yerini almıştır.  
  
 **✓ CONSIDER** uygulama <xref:System.Xml.Serialization.IXmlSerializable> ne XML serileştirme özniteliklerini uygulayarak sunulan daha serileştirilmiş XML şekli üzerinde daha fazla denetim isterseniz, arabirim. İki yöntem arabirimin <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> ve <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, tam olarak serileştirilmiş XML akışı denetlemek izin. Türü için uygulama tarafından oluşturulan XML Şeması de denetleyebilirsiniz `XmlSchemaProviderAttribute`.  
  
## <a name="supporting-runtime-serialization"></a>Çalışma zamanı serileştirme destekleme  
 Çalışma zamanı serileştirme .NET uzaktan iletişim tarafından kullanılan bir teknolojisidir. .NET uzaktan iletişim kullanarak türlerinizi taşınır düşünüyorsanız, çalışma zamanı serileştirme destekledikleri emin olmanız gerekir.  
  
 Temel destek için çalışma zamanı serileştirme uygulayarak sağlanabilir <xref:System.SerializableAttribute>, ve daha gelişmiş senaryoları içeren basit bir çalışma zamanı seri hale getirilebilir deseni uygulama (uygulama <xref:System.Runtime.Serialization.ISerializable> ve seri hale getirme Oluşturucu sağlayın).  
  
 **✓ CONSIDER** türlerinizi .NET uzaktan iletişim ile kullanılacaksa, çalışma zamanı serileştirme destekleme. Örneğin, <xref:System.AddIn?displayProperty=nameWithType> ad alanı .NET uzaktan iletişim kullanır ve tüm türleri değiştirilen arasında `System.AddIn` add-INS çalışma zamanı serileştirme desteklemesi gerekir.  
  
 **✓ CONSIDER** seri hale getirme işlemi üzerinde tam denetimi istiyorsanız çalışma zamanı seri hale getirilebilir düzeni uygulama. Verileri olarak dönüştürmek istiyorsanız, örneğin, dosya serileştirilmiş seri durumdan veya.  
  
 Düzen çok basit yöneliktir. Tek yapmak için ihtiyacınız olan uygulayan <xref:System.Runtime.Serialization.ISerializable> arabirim ve nesnenin seri durumda olduğunda kullanılan özel bir oluşturucu sağlayın.  
  
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
  
 **✓ DO** bir bağlantı isteği uygulamak <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> uygulaması. Bu, yalnızca tam olarak çekirdek ve çalışma zamanı seri hale getirici üye erişimi güvenilir sağlar.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
