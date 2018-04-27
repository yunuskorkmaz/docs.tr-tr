---
title: Serialization1
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 14b2f596245eb7f9cdcb9b3e30eeb100180cd793
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="serialization"></a>Serileştirme
Seri hale getirme nesneyi kullanıma kalıcı veya taşınan bir biçime dönüştürme işlemidir. Örneğin, bir nesneyi serileştirme, HTTP kullanarak ve hedef makinenin seri Internet üzerinden taşıma.  
  
 .NET Framework çeşitli serileştirme senaryolar için iyileştirilen üç ana serileştirme teknolojiler sunar. Aşağıdaki tablo, bu teknolojiler ve bu teknolojiler için ilgili ana Framework türleri listeler.  
  
|**Teknoloji ad**|**Ana türleri**|**Senaryoları**|  
|-------------------------|--------------------|-------------------|  
|**Veri sözleşmesi seri hale getirme**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Genel kalıcılığı<br />Web Hizmetleri<br />JSON|  
|**XML serileştirme**|<xref:System.Xml.Serialization.XmlSerializer>|XML biçiminde XML şeklini üzerinde tam denetim|  
|**Çalışma zamanı serileştirme (ikili ve SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET uzaktan iletişim|  
  
 **✓ YAPMAK** yeni türleri tasarlarken serileştirme düşünün.  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>Destek için sağ serileştirme teknolojiyi seçmenizde  
 **✓ DÜŞÜNÜN** türünüz örneklerini kalıcı veya Web Hizmetleri içinde kullanılan gerekebilir, veri sözleşmesi seri hale getirme destekleme.  
  
 **✓ DÜŞÜNÜN** türü serileştirildiğinde üreten XML biçimi hakkında daha fazla denetime ihtiyacınız varsa XML serileştirme yerine veya veri sözleşmesi seri hale getirme ek destek.  
  
 Veri sözleşmesi seri hale getirme tarafından XML özniteliği üretmek için örneğin, desteklenmeyen bir XML kullanmanıza gerek olduğu senaryolar oluşturmak bazı birlikte çalışabilirlik gerekli olabilir.  
  
 **✓ DÜŞÜNÜN** türünüz örnekleri .NET uzaktan iletişim sınırlarında seyahat gerekiyorsa çalışma zamanı serileştirme destekleme.  
  
 **KAÇININ x** çalışma zamanı serileştirme veya XML serileştirme yalnızca genel Kalıcılık nedenlerle destekleme. Veri sözleşmesi seri hale getirme yerine tercih eder.  
  
## <a name="supporting-data-contract-serialization"></a>Destekleyici veri sözleşmesi seri hale getirme  
 Türlerini destekleyebilir veri sözleşmesi seri hale getirme uygulayarak <xref:System.Runtime.Serialization.DataContractAttribute> türüne ve <xref:System.Runtime.Serialization.DataMemberAttribute> türü üyeleri (alanları ve özellikleri).  
  
 **✓ DÜŞÜNÜN** türü kısmi güvende kullanılabiliyorsa, genel türde veri üyeleri işaretleme.  
  
 Tam güven veri sözleşmesi serileştiricileri seri hale getirmek ve seri durumdan ortak olmayan türleri ve üyeleri, ancak yalnızca Genel üyeler sıralanabilir ve kısmi güvende serisi.  
  
 **✓ YAPMAK** bir alıcı ve ayarlayıcıya sahip tüm özellikleri uygulamak <xref:System.Runtime.Serialization.DataMemberAttribute>. Veri sözleşmesi serileştiricileri hem alıcı hem de ayarlayıcı türü seri hale getirilebilir kabul edilmesi gerektirir. (.NET Framework 3.5 SP1'de, bazı koleksiyon özellikleri salt alma olabilir.) Kısmi güvende türü kullanılmaz, bir veya iki özellik erişimcisi ortak olmayan olabilir.  
  
 **✓ DÜŞÜNÜN** seri durumdan çıkarılmış örneklerinin başlatma için seri hale getirme geri çağrıları kullanarak.  
  
 Nesneleri seri olduğunda oluşturucular çağrılır değil. (Kuralına özel durumlar vardır. Koleksiyonların oluşturucular işaretlenmiş <xref:System.Runtime.Serialization.CollectionDataContractAttribute> seri kaldırma sırasında çağrılır.) Bu nedenle, normal oluşturma sırasında yürütür herhangi bir mantık seri hale getirme geri çağrıları biri olarak uygulanması gerekir.  
  
 `OnDeserializedAttribute` en yaygın kullanılan geri çağırma özniteliğidir. Ailesindeki diğer öznitelikleri <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute>, ve <xref:System.Runtime.Serialization.OnSerializedAttribute>. Seri durumundan çıkarma, serileştirme önce ve son olarak seri hale getirme sonra önce sırasıyla yürütülen geri çağırmaları işaretlemek için kullanılabilir.  
  
 **✓ DÜŞÜNÜN** kullanarak <xref:System.Runtime.Serialization.KnownTypeAttribute> karmaşık nesne grafiğinin seri durumdan çıkarılırken kullanılmalıdır somut türleri belirtmek için.  
  
 **✓ YAPMAK** oluştururken veya seri hale getirilebilir türler değiştirme ileriye ve geriye dönük uyumluluk göz önünde bulundurun.  
  
 Türünüz gelecek sürümlerinde akışları serileştirilmiş unutmayın türü geçerli sürüme serisi ve bunun tam tersi.  
  
 Veri sözleşmesi öznitelikleri için açık parametrelerini kullanarak sözleşme korumak için özellikle dikkatli geçen sürece veri üyeleri, özel ve iç, bile adlarını, türlerini veya bile sıralarına türü gelecekteki sürümlerinde değiştiremezsiniz anladığınızdan emin olun .  
  
 Seri hale getirme uyumluluğu için seri hale getirilebilir türler değişiklik yaparken sınayın. Yeni sürümü eski bir sürümüne seri durumdan deneyin ve tersi.  
  
 **✓ DÜŞÜNÜN** uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> türü farklı sürümleri arasında gidiş izin vermek için.  
  
 Arabirim gidiş sırasında veri kaybı olmamasına emin olmak seri hale getirici sağlar. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> Özelliği geçerli sürüme bilinmiyor türü gelecekteki sürümünden herhangi bir veriyi depolamak için kullanılır ve bu nedenle onu depolayamaz, kendi veri üyeleri. Geçerli sürüm sonradan serileştirilen ve gelecekteki bir sürümüne seri, ek verileri seri hale getirilmiş akışta kullanılabilir.  
  
## <a name="supporting-xml-serialization"></a>XML serileştirme destekleme  
 Veri sözleşmesi seri hale getirme (varsayılan) ana olan .NET Framework serileştirme teknolojisinde vardır, ancak veri sözleşmesi seri hale getirme desteklemediği serileştirme senaryoları. Örneğin, bunu, üretilen veya seri hale getirici tarafından tüketilen XML şekli üzerinde tam denetim sağlamaz. Böyle bir ince denetim gerekiyorsa, kullanılacak XML serileştirme sahiptir ve bu serileştirme teknolojisini desteklemek için türlerinizi tasarlamanız gerekir.  
  
 **KAÇININ x** XML şeklini denetlemek için çok güçlü bir nedeniniz yoksa, türlerinizi XML serileştirmesi için özellikle tasarlama üretilen. Veri sözleşmesi önceki bölümde açıklanan seri hale getirme bu serileştirme teknoloji almıştır.  
  
 **✓ DÜŞÜNÜN** uygulama <xref:System.Xml.Serialization.IXmlSerializable> ne XML serileştirme özniteliklerini uygulayarak sunulan daha serileştirilmiş XML şekli üzerinde daha fazla denetim isterseniz, arabirim. İki yöntem arabiriminin <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> ve <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, tam olarak serileştirilmiş XML akışı denetlemenize olanak sağlar. Türü için uygulanarak oluşturulan XML Şeması kontrol edebilirsiniz `XmlSchemaProviderAttribute`.  
  
## <a name="supporting-runtime-serialization"></a>Çalışma zamanı serileştirme destekleme  
 Çalışma zamanı serileştirme .NET uzaktan iletişim tarafından kullanılan bir teknolojidir. .NET uzaktan iletişim kullanarak türlerinizi taşınır düşünüyorsanız, çalışma zamanı serileştirme desteklediğinden emin olmanız gerekir.  
  
 Çalışma zamanı serileştirme için temel destek uygulayarak sağlanabilir <xref:System.SerializableAttribute>, ve daha Gelişmiş senaryolar içeren basit bir çalışma zamanı seri hale getirilebilir düzeni uygulama (uygulama <xref:System.Runtime.Serialization.ISerializable> ve seri hale getirme Oluşturucusu sağlar).  
  
 **✓ DÜŞÜNÜN** türlerinizi .NET uzaktan iletişim ile kullanılacaksa, çalışma zamanı serileştirme destekleme. Örneğin, <xref:System.AddIn?displayProperty=nameWithType> ad alanı .NET uzaktan iletişim kullanır ve böylece tüm türleri akar arasında `System.AddIn` eklentileri gereken çalışma zamanı serileştirme desteklemek.  
  
 **✓ DÜŞÜNÜN** seri hale getirme işlemi üzerinde tam denetimi istiyorsanız çalışma zamanı seri hale getirilebilir düzeni uygulama. Örneğin, verileri olarak dönüştürmek istiyorsanız seri durumdan veya serileştirilir.  
  
 Düzen çok basit yöneliktir. Yapmanız gereken tek şey uygulamak <xref:System.Runtime.Serialization.ISerializable> arabirim ve nesnenin seri durumda olduğunda kullanılan özel bir oluşturucu sağlayın.  
  
 **✓ YAPMAK** korumalı serileştirme Oluşturucusu oluşturarak yazılan ve tam olarak burada aşağıdaki örnekte gösterildiği gibi adlı iki parametre sağlayabilirsiniz.  
  
```  
[Serializable]  
public class Person : ISerializable {  
    protected Person(SerializationInfo info, StreamingContext context) {  
        ...  
    }  
}  
```  
  
 **✓ YAPMAK** uygulamak `ISerializable` üyeleri açıkça.  
  
 **✓ YAPMAK** bir bağlantı isteği uygulamak <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> uygulaması. Bu, yalnızca tam olarak çekirdek ve çalışma zamanı seri hale getirici üye erişimi güvenilir sağlar.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
