---
title: "Talep tabanlı yetkilendirme WIF kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e24000a3-8fd8-4c0e-bdf0-39882cc0f6d8
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: bc6a9d828f1ab666ddda687931785f3853b74374
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="claims-based-authorization-using-wif"></a>Talep tabanlı yetkilendirme WIF kullanma
Bağlı taraf uygulamasında, yetkilendirme kimliği doğrulanmış bir kimliğin hangi kaynaklara erişebileceğini ve bu kaynaklar üzerinde hangi işlemleri gerçekleştirebileceğini belirler. Uygunsuz veya zayıf yetkilendirme, bilgi ifşasına ve verilerin izinsiz kullanımına neden olur. Bu konuda, Windows Identity Foundation (WIF) ve Microsoft Azure Erişim Denetimi Hizmeti (ACS) gibi Güvenlik Belirteci Hizmeti (STS) kullanılarak talep kullanan ASP.NET web uygulamaları ve hizmetleri için yetkilendirme uygulama yaklaşımları açıklanmaktadır.  
  
## <a name="overview"></a>Genel Bakış  
 İlk sürümünden bu yana, .NET Framework yetkilendirmenin uygulanması için esnek bir mekanizma sunmuştur. Bu mekanizma iki basit arabirimlere dayalı —**IPrincipal** ve **IIdentity**. Somut uygulamaları **IIdentity** kimliği doğrulanmış bir kullanıcı temsil eder. Örneğin, **WindowsIdentity** uygulamasını temsil eder, Active Directory tarafından kimliği doğrulanmış bir kullanıcı ve **Genericıdentity** özel bir kimliği doğrulanmış bir kullanıcı temsil eder kimlik doğrulama işlemi. Somut uygulamaları **IPrincipal** bağlı olarak rol deposu rollerini kullanarak izinlerini denetlemek için Yardım. Örneğin, **WindowsPrincipal** denetler **WindowsIdentity** Active Directory gruplarının üyeliği için. Bu onay çağırarak gerçekleştirilen **IsInRole** yöntemi **IPrincipal** arabirimi. Rollere göre erişim denetimine Rol Tabanlı Erişim Denetimi (RBAC) adı verilir. Daha fazla bilgi için bkz: [rol tabanlı erişim denetimi](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_1).  Talepler, benzer, rol tabanlı yetkilendirme mekanizmalarını desteklemek amacıyla roller hakkında bilgi taşımak için kullanılabilir.  
  
 Talepler, rollerin ötesinde daha karmaşık yetkilendirme kararlarının verilmesini sağlamak için de kullanılabilir. Talepler kullanıcı - yaşı, posta kodu, ayakkabı boyutu vb. hakkında neredeyse tüm bilgi temel alabilir. Rastgele taleplerine dayalı erişim denetimi mekanizması talep tabanlı yetkilendirme denir. Daha fazla bilgi için bkz: [talep tabanlı yetkilendirme](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_2).  
  
<a name="BKMK_1"></a>   
## <a name="role-based-access-control"></a>Rol Tabanlı Erişim Denetimi  
 RBAC, kullanıcı izinlerinin yönetildiği ve kullanıcı rollerine göre bir uygulama tarafından zorlanan yetkilendirme yaklaşımıdır. Kullanıcının bir eylemi gerçekleştirmesi gereken rolü varsa, erişim verilir; aksi takdirde, erişim engellenir.  
  
### <a name="iprincipalisinrole-method"></a>IPrincipal.IsInRole Yöntemi  
 Talep kullanan uygulamalarda RBAC yaklaşımı uygulamak için kullandığınız **IsInRole()** yönteminde **IPrinicpal** talep kullanan olmayan uygulamalarda gibi arabirim. Kullanmanın birkaç yolu vardır **IsInRole()** yöntemi:  
  
-   Açıkça çağrılması **IPrincipal.IsInRole("Administrator")**. Bu yaklaşımda, sonuç olarak Boole değeri elde edilir. Kendi koşullu deyimlerinizde kullanın. Kodunuzdaki herhangi bir yerde rasgele kullanılabilir.  
  
-   Güvenlik talep kullanarak **PrincipalPermission.Demand()**. Bu yaklaşımda, talep karşılanmazsa sonuç olarak bir özel durum elde edilir. Bu, özel durum işleme stratejinizle uyumlu olmalıdır. Özel durumları atma Boole değeri döndürmek için kıyasla performans açısından daha pahalı olması. Bu, kodunuzdaki herhangi bir yerde kullanılabilir.  
  
-   Bildirim temelli özniteliklerini kullanarak **[PrincipalPermission (SecurityAction.Demand, Role = "Yönetici")]**. Bu yaklaşıma, yöntemleri donatmak için kullanıldığından bildirim temelli denir. Yöntem uygulamalarının içindeki kod bloklarında kullanılamaz. Talep karşılanmazsa sonuç olarak bir özel durum elde edilir. Özel durum işleme stratejinizle uyumlu olduğundan emin olmanız gerekir.  
  
-   URL yetkilendirmesi kullanarak, kullanarak  **\<yetkilendirme >** bölümüne **web.config**. Bu yaklaşım, yetkilendirme URL düzeyinde yönetilirken uygundur. Bu, daha önce bahsedilenler arasında en genel düzeydir. Bu yaklaşımın avantajı, değişikliklerin yapılandırma dosyasında yapılması, yani değişiklikten yararlanmak için kodun derlenmesine gerek olmamasıdır.  
  
### <a name="expressing-roles-as-claims"></a>Rolleri Talepler Olarak İfade Etme  
 Zaman **IsInRole()** yöntemi çağrıldığında, geçerli kullanıcının bu rolün olup olmadığını görmek için yapılan bir denetim yoktur. Talep kullanan uygulamalarda, rol belirteçte kullanılabilir olması gereken bir rol talep türü olarak ifade edilir. Rol talep türü, aşağıdaki URI kullanılarak ifade edilir:  
  
 http://schemas.microsoft.com/ws/2008/06/identity/claims/role  
  
 Bir belirteci rol talep türüyle zenginleştirmenin birkaç yöntemi vardır:  
  
-   **Belirteç verme sırasında**. Bir kullanıcının kimliği doğrulandığında veya Federasyon sağlayıcısı Microsoft Azure erişim denetimi Hizmeti'nden (ACS) gibi kimlik sağlayıcısı STS tarafından rol talep verilebilir.  
  
-   **Talep rolü türü ClaimsAuthenticationManager kullanarak rastgele taleplerine dönüştürme**. ClaimsAuthenticationManager, WIF'nin bir parçası olarak sunulan bir bileşendir. Uygulama başlattıklarında isteklerin kesilmesini sağlar, belirteçleri denetler ve talepleri ekleyerek, değiştirerek veya kaldırarak dönüştürür. Talep dönüştürme için ClaimsAuthenticationManager kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: uygulama rol tabanlı erişim denetimi (RBAC) talep kullanan ASP.NET uygulaması kullanarak WIF ve ACS](http://go.microsoft.com/fwlink/?LinkID=247445) (http://go.microsoft.com/ fwlink /? LinkId 247444 =).  
  
-   **SamlSecurityTokenRequirement yapılandırma bölümünü kullanmayı rol türü için rasgele talep eşleme**— talep dönüştürme burada yapılır bildirim temelli bir yaklaşım yalnızca yapılandırmasını ve hiçbir kodlama kullanılarak gereklidir.  
  
<a name="BKMK_2"></a>   
## <a name="claims-based-authorization"></a>Beyana Dayalı Yetkilendirme  
 Beyana dayalı yetkilendirme, erişim verme veya reddetmeye yönelik yetkilendirme kararının, karar verme beyanlarında yer alan verileri kullanan rasgele mantığı temel aldığı bir yaklaşımdır. RBAC söz konusu olduğunda, kullanılan tek talebin rol türü talep olduğunu hatırlayın. Rol türü talep, kullanıcının belirli role ait olup olmadığını denetlemek için kullanıldı. Beyana dayalı yetkilendirme yaklaşımını kullanarak yetkilendirme kararı verme sürecini anlamak için aşağıdaki adımları göz önünde bulundurun:  
  
1.  Uygulama, kullanıcının kimliğinin doğrulanmasını gerektiren bir istek alır.  
  
2.  WIF, kullanıcıyı kimlik sağlayıcısına yönlendirir, kimliği doğrulandıktan sonra kullanıcıyı temsil eden ve kullanıcı hakkında talepler içeren ilişkili bir güvenlik belirteciyle uygulama isteği yapılır. WIF, bu talepleri kullanıcıyı temsil eden sorumluyla ilişkilendirir.  
  
3.  Uygulama, talepleri karar mantığı mekanizmasına geçirir. Bu; bellek içi kod, web hizmeti çağrısı, veritabanı sorgusu, gelişmiş bir kural altyapısı veya ClaimsAuthorizationManager kullanımı olabilir.  
  
4.  Karar mekanizması taleplere göre sonucu hesaplar.  
  
5.  Sonuç true ise erişim verilir, false ise engellenir. Örneğin, kural kullanıcının 21 yaşında veya daha yaşlı olmasını ve Washington eyaletinde yaşamasını gerektirebilir.  
  
 <xref:System.Security.Claims.ClaimsAuthorizationManager>Talep tabanlı yetkilendirme uygulamalarınızda karar mantığını harici hale getirerek için yararlıdır. ClaimsAuthorizationManager, .NET 4.5'in bir parçası olarak sunulan bir WIF bileşenidir. ClaimsAuthorizationManager, gelen taleplere göre yetkilendirme kararları vermek için gelen istekleri kesmenize ve istediğiniz mantığı uygulamanıza imkan tanır. Bu, yetkilendirme mantığının değiştirilmesi gerektiğinde önemli hale gelir. Bu durumda, ClaimsAuthorizationManager uygulamanın bütünlüğünü etkilemez ve bu nedenle değişikliğin sonucu olarak uygulama hatası oluşma olasılığını azaltır. Talep tabanlı erişim denetimi için ClaimsAuthorizationManager kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: uygulama talep yetkilendirme talep kullanan ASP.NET uygulaması kullanarak WIF ve ACS](http://go.microsoft.com/fwlink/?LinkID=247446).
