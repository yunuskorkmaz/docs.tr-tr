---
description: 'Daha fazla bilgi edinin: kısmi güven En Iyi uygulamaları'
title: Kısmi Güven En İyi Uygulamaları
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: abdc0fbbb84581b302bca8d514a5f8f5cc2703e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733560"
---
# <a name="partial-trust-best-practices"></a>Kısmi Güven En İyi Uygulamaları

Bu konuda kısmi güven ortamında Windows Communication Foundation (WCF) çalıştırılırken en iyi yöntemler açıklanmaktadır.

## <a name="serialization"></a>Serileştirme

<xref:System.Runtime.Serialization.DataContractSerializer>' İ kısmen güvenilen bir uygulamada kullanırken aşağıdaki yöntemleri uygulayın.

- Tüm serileştirilebilir türler açıkça `[DataContract]` özniteliğiyle işaretlenmelidir. Aşağıdaki teknikler kısmi güven ortamında desteklenmez:

- Sınıfları ile serileştirilmesi için İşaretleme <xref:System.SerializableAttribute> .

- <xref:System.Runtime.Serialization.ISerializable>Bir sınıfa serileştirme işlemini denetlemesine izin vermek için arabirimi uygulama.

### <a name="using-datacontractserializer"></a>DataContractSerializer kullanma

- Özniteliğiyle işaretlenen tüm türler `[DataContract]` ortak olmalıdır. Genel olmayan türler kısmi güven ortamında serileştirilemiyor.

- `[DataContract]`Serileştirilebilir türdeki tüm Üyeler `[DataContract]` ortak olmalıdır. Genel olmayan bir tür `[DataMember]` kısmi güven ortamında serileştirilemiyor.

- Serileştirme olaylarını işleyen Yöntemler (örneğin,, `OnSerializing` `OnSerialized` `OnDeserializing` ve `OnDeserialized` ) ortak olarak bildirilmelidir. Ancak, hem açık hem de örtük uygulamaları <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> desteklenir.

- `[DataContract]` ile işaretlenen derlemelerde uygulanan türler, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> <xref:System.Runtime.Serialization.DataContractSerializer> seri durumdan çıkarma sırasında yeni örneklendirilmiş nesnenin oluşturucusunu çağırmadığından tür oluşturucusunda güvenlikle ilgili eylemleri gerçekleştirmemelidir. Özellikle, aşağıdaki ortak güvenlik teknikleri türler için kaçınılmalıdır `[DataContract]` :

- Türün oluşturucusunu iç veya özel hale getirerek kısmi güven erişimini kısıtlamaya çalışılıyor.

- Türün oluşturucusuna bir ekleyerek türe erişimi sınırlandırma `[LinkDemand]` .

- Nesnesi başarıyla örneklendiği için, Oluşturucu tarafından zorlanan tüm doğrulama denetimleri başarıyla geçildi.

### <a name="using-ixmlserializable"></a>IXmlSerializable kullanma

Aşağıdaki en iyi uygulamalar <xref:System.Xml.Serialization.IXmlSerializable> , uygulayan ve kullanılarak serileştirilmiş olan türler için geçerlidir <xref:System.Runtime.Serialization.DataContractSerializer> :

- <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A>Statik yöntem uygulamaları olmalıdır `public` .

- Arabirimi uygulayan örnek yöntemleri olmalıdır <xref:System.Xml.Serialization.IXmlSerializable> `public` .

## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>Kısmen güvenilen çağıranların çağrılarına Izin veren Fully-Trusted platform kodundan WCF kullanma

WCF kısmi güven güvenlik modeli, bir WCF genel yönteminin veya özelliğinin, barındırma uygulamasının kod erişim güvenliği (CAS) bağlamında çalıştığını varsayar. WCF Ayrıca her biri için yalnızca bir uygulama güvenlik bağlamının olduğunu <xref:System.AppDomain> ve bu bağlamın <xref:System.AppDomain> Güvenilen bir ana bilgisayar tarafından oluşturma zamanında (örneğin, ASP.NET uygulama Yöneticisi tarafından yapılan bir çağrıya göre) oluşturulduğunu varsayar <xref:System.AppDomain.CreateDomain%2A> .

Bu güvenlik modeli, orta düzey güven ASP.NET uygulamasında çalışan Kullanıcı kodu gibi ek CA izinleri içermeyen Kullanıcı tarafından yazılmış uygulamalar için geçerlidir. Ancak, tam güvenilir platform kodu (örneğin, genel derleme önbelleğinde yüklü olan ve kısmen güvenilen koddan yapılan çağrıları kabul eden bir üçüncü taraf derleme), uygulama düzeyinde güvenlik açıklarına giriş yapmaktan kaçınmak için kısmen güvenilen bir uygulama adına WCF 'ye çağrı yaparken açık bir işlem olmalıdır.

Tam güven kodu, <xref:System.Security.PermissionSet.Assert%2A> <xref:System.Security.PermissionSet.PermitOnly%2A> <xref:System.Security.PermissionSet.Deny%2A> WCF API 'lerini kısmen güvenilen kod adına çağrılmadan önce GEÇERLI iş parçacığının CAS izin kümesini (, veya çağırarak) değiştirmekten kaçınmalıdır. Uygulama düzeyi güvenlik içeriğinden bağımsız olan iş parçacığına özgü izin bağlamını ele almak, reddetmek veya başka bir şekilde oluşturmak beklenmedik davranışa neden olabilir. Uygulamaya bağlı olarak bu davranış, uygulama düzeyinde güvenlik açıklarına neden olabilir.

İş parçacığına özgü bir izin bağlamı kullanarak WCF 'ye çağıran kod, ortaya çıkabilecek aşağıdaki durumları işleyecek şekilde hazırlanmalıdır:

- İş parçacığına özgü güvenlik bağlamı işlemin süresi boyunca tutulmayabilir, bu da olası güvenlik özel durumlarına neden olur.

- İç WCF kodu ve Kullanıcı tarafından sağlanmış geri çağrılar, çağrının ilk olarak başlatıldığı sunucudan farklı bir güvenlik bağlamında çalıştırılabilir. Bu bağlamlar şunlardır:

  - Uygulama izin bağlamı.

  - O sırada çalışmakta olan diğer Kullanıcı iş parçacıkları tarafından daha önce oluşturulan ve o anda çalışan kullanım ömrü boyunca WCF 'ye çağrı yapmak için kullanılan iş parçacığına özgü izin bağlamı <xref:System.AppDomain>

WCF genel API 'Lerine çağrılmadan önce, bu izinler tam güvenilir bir bileşen tarafından belirtilmemişse, kısmen güvenilen kodun tam güven izinleri edinemediğini garanti eder. Ancak, tam güveni ele almak için etkileri belirli bir iş parçacığı, işlem veya kullanıcı eylemine yalıtılmış olduğunu garanti etmez.

En iyi uygulama olarak,, veya çağırarak iş parçacığına özgü izin bağlamı oluşturmaktan <xref:System.Security.PermissionSet.Assert%2A> kaçının <xref:System.Security.PermissionSet.PermitOnly%2A> <xref:System.Security.PermissionSet.Deny%2A> . Bunun yerine,, veya gerekli olmaması için, uygulamanın kendisi için ayrıcalık verin veya <xref:System.Security.PermissionSet.Assert%2A> reddedin <xref:System.Security.PermissionSet.Deny%2A> <xref:System.Security.PermissionSet.PermitOnly%2A> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
