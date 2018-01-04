---
title: "Kısmi Güven En İyi Uygulamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 817f7aeeb7adece1c375bb8b0cc455a17fb54185
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="partial-trust-best-practices"></a>Kısmi Güven En İyi Uygulamaları
Bu konu çalışırken en iyi uygulamaları açıklar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kısmi güven ortamında.  
  
## <a name="serialization"></a>Serileştirme  
 Kullanırken aşağıdaki yöntemleri uygulayın <xref:System.Runtime.Serialization.DataContractSerializer> kısmen güvenilen uygulamada.  
  
-   Tüm seri hale getirilebilir türler ile açıkça işaretlenmelidir `[DataContract]` özniteliği. Aşağıdaki teknikler, kısmi güven ortamında desteklenmez:  
  
-   İle serileştirilecek sınıfları işaretleme <xref:System.SerializableAttribute>.  
  
-   Uygulama <xref:System.Runtime.Serialization.ISerializable> seri hale getirme işlemini kontrol eden bir sınıf izin vermek için arabirim.  
  
### <a name="using-datacontractserializer"></a>DataContractSerializer kullanılarak  
  
-   Tüm türleri ile işaretlenen `[DataContract]` özniteliği ortak olmalıdır. Ortak olmayan türleri bir kısmi güven ortamında seri hale getirilemez.  
  
-   Tüm `[DataContract]` üyeleri bir serileştirilebilir `[DataContract]` türü ortak olmalıdır. Genel olmayan bir türüyle `[DataMember]` bir kısmi güven ortamında seri hale getirilemez.  
  
-   Seri hale getirme olayları işlemek yöntemleri (gibi `OnSerializing`, `OnSerialized`, `OnDeserializing`, ve `OnDeserialized`) genel olarak bildirilmelidir. Ancak, açık ve kapalı uygulamaları <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> desteklenir.  
  
-   `[DataContract]`derlemelerde uygulanan türleri ile işaretlenen <xref:System.Security.AllowPartiallyTrustedCallersAttribute> Tür oluşturucu Eylemler güvenlikle ilgili olarak gerçekleştirmelisiniz değil <xref:System.Runtime.Serialization.DataContractSerializer> Oluşturucusu yeni örneği nesnesinin seri durumdan çıkarma sırasında çağırmaz. Özellikle, aşağıdaki genel güvenlik teknikleri için kaçınılmalıdır `[DataContract]` türleri:  
  
-   İç veya özel tür Oluşturucu yaparak kısmi güven erişimi kısıtlamak çalışıyor.  
  
-   Ekleyerek türü için erişimi kısıtlamak bir `[LinkDemand]` tür oluşturucuya.  
  
-   Nesne başarıyla örneği olduğundan oluşturucusu tarafından zorlanan tüm doğrulama denetimleri başarıyla başarılı olduğunu varsayarak.  
  
### <a name="using-ixmlserializable"></a>IXmlSerializable kullanma  
 Uygulama türleri için aşağıdaki en iyi yöntemleri uygulayın <xref:System.Xml.Serialization.IXmlSerializable> ve kullanılarak serileştirilmiş <xref:System.Runtime.Serialization.DataContractSerializer>:  
  
-   <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> Statik yöntem uygulamalarını olmalıdır `public`.  
  
-   Uygulama örnek yöntemleri <xref:System.Xml.Serialization.IXmlSerializable> arabirimi olmalıdır `public`.  
  
## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>WCF gelen çağrıları kısmen sağlayan tam olarak Güvenilir Platform kodundan kullanarak güvenilen arayanlara  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Kısmi güven güvenlik modeli varsayar, tüm çağıran bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ortak yöntemi veya özelliği barındırma uygulama kod erişim güvenliği (CAS) bağlamında çalışır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Ayrıca, yalnızca bir uygulama güvenlik bağlamı var her biri için varsayar <xref:System.AppDomain>, ve bu bağlamda adresindeki oluşturulmuş <xref:System.AppDomain> bir güvenilir ana bilgisayar tarafından oluşturma zamanı (örneğin, bir çağrı tarafından <xref:System.AppDomain.CreateDomain%2A> veya ASP.NET Uygulama Yöneticisi tarafından).  
  
 Bu güvenlik modeli, bir orta güven ASP.NET uygulamasında çalışan kullanıcı kodu gibi ek CA'lar izinler assert olamaz kullanıcı tarafından yazılan uygulamaları için geçerlidir. Ancak, tam olarak güvenilir platform kodu (örneğin, genel derleme önbelleğinde yüklü olan ve kısmen güvenilen kod gelen çağrıları kabul eden bir üçüncü taraf derleme) açık içine çağrılırken özen gerekir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kısmen güvenilen bir adına Uygulama düzeyi güvenlik açıkları önlemek için uygulama.  
  
 Tam güven kodlardan kaçının geçerli iş parçacığının CA'lar izin kümesini değiştirme (çağırarak <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, veya <xref:System.Security.PermissionSet.Deny%2A>) çağrılmadan önce [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kısmen güvenilen kod adına API'leri. Sunduğundan, engelleme ya da aksi takdirde uygulama düzeyinde güvenlik bağlamı bağımsız olan bir iş parçacığına özgü izni bağlamı oluşturma beklenmeyen davranışlara neden olabilir. Uygulamaya bağlı olarak, bu davranış, uygulama düzeyinde güvenlik açıklarına neden olabilir.  
  
 İçine çağıran kodu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iş parçacığına özgü izni bağlamını kullanarak gerekir hazırlanmış kaynaklanabilecek aşağıdaki durumlarda işlemek için:  
  
-   İş parçacığına özgü güvenlik bağlamı olası güvenlik özel durumlarıyla sonuçları işlemi süresince saklanması değil.  
  
-   İç [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kodun yanı sıra tüm kullanıcı tarafından sağlanan geri aramalar farklı güvenlik bağlamı altında çağrı başlangıçta başlatıldı fazla çalışabilir. Bu içerikler şunları içerir:  
  
    -   Uygulama izni bağlamı.  
  
    -   Daha önce çağırmak için kullanılan başka bir kullanıcı iş parçacığı tarafından oluşturulan her iş parçacığına özgü izni bağlam [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] şu anda çalışan kullanım ömrü süresince <xref:System.AppDomain>.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bu izinlere içine çağrılmadan önce tam olarak güvenilir bir bileşen tarafından uygulanan sürece kısmen güvenilen kodu tam güven izinleri elde edemiyor garanti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ortak API'ler. Ancak, onu tam güven sunduğundan etkilerini belirli iş parçacığı, işlem veya kullanıcı eylemi yalıtılmış garanti etmez.  
  
 En iyi uygulama, iş parçacığına özgü izni bağlam çağırarak oluşturmamak <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, veya <xref:System.Security.PermissionSet.Deny%2A>. Bunun yerine, vermek ya da uygulamaya kendisini ayrıcalık reddetmek için hiçbir <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A>, veya <xref:System.Security.PermissionSet.PermitOnly%2A> gereklidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.IXmlSerializable>
