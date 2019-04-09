---
title: Kısmi Güven En İyi Uygulamaları
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: c83c36020cfd5b41e99ff9eeb7968d0b5df909a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184086"
---
# <a name="partial-trust-best-practices"></a>Kısmi Güven En İyi Uygulamaları
Bu konu, Windows Communication Foundation (WCF) bir kısmi güven ortamında çalışırken en iyi uygulamaları açıklar.  
  
## <a name="serialization"></a>Serileştirme  
 Aşağıdaki yöntemleri kullanılırken geçerli <xref:System.Runtime.Serialization.DataContractSerializer> kısmen güvenilen uygulamada.  
  
-   Tüm serializable türler ile açıkça işaretlenmelidir `[DataContract]` özniteliği. Aşağıdaki tekniklerden bir kısmi güven ortamında desteklenmez:  
  
-   İle serileştirilecek sınıflar işaretleme <xref:System.SerializableAttribute>.  
  
-   Uygulama <xref:System.Runtime.Serialization.ISerializable> , seri hale getirme işlemini denetlemek bir sınıf izin vermek için arabirim.  
  
### <a name="using-datacontractserializer"></a>DataContractSerializer kullanarak  
  
-   Tüm türleri ile işaretlenen `[DataContract]` özniteliği genel olmalıdır. Kısmi güven ortamında genel olmayan türler seri hale getirilemiyor.  
  
-   Tüm `[DataContract]` seri hale getirilebilir bir üye `[DataContract]` türü ortak olmalıdır. Genel olmayan bir türle `[DataMember]` bir kısmi güven ortamında nelze serializovat.  
  
-   Serileştirme olayları işleyen yöntemler (gibi `OnSerializing`, `OnSerialized`, `OnDeserializing`, ve `OnDeserialized`) genel olarak bildirilmelidir. Ancak, açık ve örtük uygulamaları <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> desteklenir.  
  
-   `[DataContract]` derlemelerde uygulanan türleri ile işaretlenen <xref:System.Security.AllowPartiallyTrustedCallersAttribute> Tür oluşturucu Eylemler ile ilgili olarak gerçekleştirmemelisiniz <xref:System.Runtime.Serialization.DataContractSerializer> oluşturucusu, yeni oluşturulan nesne seri durumundan çıkarma sırasında çağırmaz. Özellikle, aşağıdaki yaygın güvenlik teknikleri için kaçınılmalıdır `[DataContract]` türleri:  
  
-   İç veya özel tür Oluşturucu yaparak kısmi güven erişimi kısıtlamak çalışıyor.  
  
-   Türüne ekleyerek erişimini bir `[LinkDemand]` türün Oluşturucusu.  
  
-   Nesne başarıyla örneği olduğundan, Oluşturucu tarafından zorlanan herhangi bir doğrulama denetimleri başarıyla başarılı olduğunu varsayarak.  
  
### <a name="using-ixmlserializable"></a>IXmlSerializable kullanma  
 Uygulayan türler için aşağıdaki en iyi uygulama <xref:System.Xml.Serialization.IXmlSerializable> ve kullanılarak serileştirilmiş <xref:System.Runtime.Serialization.DataContractSerializer>:  
  
-   <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> Statik yöntem uygulamaları olmalıdır `public`.  
  
-   Uygulayan örnek yöntemler <xref:System.Xml.Serialization.IXmlSerializable> arabirimi olmalıdır `public`.  
  
## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>WCF çağrılarından kısmen sağlayan tam olarak güvenilen koddan kullanarak güvenilen Arayanların  
 WCF kısmi güven güvenliği modeli, herhangi bir WCF genel yöntem veya özellik çağıran kod erişim güvenliği (CAS) barındırma uygulama bağlamında çalıştığını varsayar. WCF ayrıca varsayar, yalnızca bir uygulama güvenlik bağlamı her biri için mevcut <xref:System.AppDomain>, ve bu bağlam, belirlenen <xref:System.AppDomain> oluşturma zamanı tarafından güvenilen bir konak (örneğin, bir çağrı tarafından <xref:System.AppDomain.CreateDomain%2A> veya ASP.NET Uygulama Yöneticisi tarafından).  
  
 Bu güvenlik modeli Orta güven ASP.NET uygulama içinde çalışan kullanıcı kodu gibi ek CAS izinler assert olamaz, kullanıcı tarafından yazılan uygulamalar için geçerlidir. Ancak, tam olarak güvenilen kod (örneğin, genel derleme önbelleğinde yüklü ve kısmen güvenilen koddan çağrıları kabul eden bir üçüncü taraf derleme) açık WCF kısmen güvenilen bir uygulama adına çağırırken dikkatli gerekir uygulama düzeyinde güvenlik açıklarını oluşturmaktan kaçının.  
  
 Tam güven kodu önlemek geçerli iş parçacığının CA izin kümesi değiştirme (çağırarak <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, veya <xref:System.Security.PermissionSet.Deny%2A>) kısmen güvenilen kod adına WCF API'larını çağırma önce. Sunduğundan, reddetme ya da aksi takdirde uygulama düzeyinde güvenlik bağlamı bağımsız bir iş parçacığına özgü izni bağlam oluşturma, beklenmeyen davranışlara neden olabilir. Uygulamaya bağlı olarak, bu davranış, uygulama düzeyinde güvenlik açıklarına neden olabilir.  
  
 Bir iş parçacığına özgü izni bağlamını kullanarak WCF çağırıyor kaynaklanabilecek aşağıdaki durumlarda işlemek için hazırlanması gerekir kodu:  
  
-   İş parçacığına özgü güvenlik bağlamı olası güvenlik özel durumlarıyla sonuçları işlemi süresince yönetilebilir değil.  
  
-   Hiçbir kullanıcı tarafından sağlanan geri çağırmaları yanı sıra iç WCF kodu farklı güvenlik bağlamı altında ilk çağrı başlatılan bir çalıştırabilirsiniz. Şu bağlamlarda şunlardır:  
  
    -   Uygulama izni bağlamı.  
  
    -   Şu anda çalışan ömrü boyunca WCF çağırmak için kullanılan diğer kullanıcı iş parçacıkları tarafından daha önce oluşturduğunuz her bir iş parçacığına özgü izni bağlam <xref:System.AppDomain>.  
  
 WCF sürece bu izinleri WCF genel API'leri çağrılmadan önce tam olarak güvenilen bir bileşen tarafından onaylanan kısmen güvenilen kod tam güven izinleri alınamıyor garanti eder. Ancak, tam güven sunduğundan etkilerini belirli iş parçacığı, işlem veya bir kullanıcı eylemi yalıtılmış garantilemez.  
  
 En iyi uygulama, iş parçacığına özgü izni bağlam çağırarak oluşturmamaya özen gösterin <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, veya <xref:System.Security.PermissionSet.Deny%2A>. Bunun yerine, vermek ya da uygulamanın kendisini ayrıcalık reddetmek için hiçbir <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A>, veya <xref:System.Security.PermissionSet.PermitOnly%2A> gereklidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
