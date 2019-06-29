---
title: WIF Kullanarak Talep Tabanlı Yetkilendirme
ms.date: 03/30/2017
ms.assetid: e24000a3-8fd8-4c0e-bdf0-39882cc0f6d8
author: BrucePerlerMS
ms.openlocfilehash: 9d20f8fbce916a038fc8224492a4077e1978ed8c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422365"
---
# <a name="claims-based-authorization-using-wif"></a>WIF Kullanarak Talep Tabanlı Yetkilendirme
Bağlı taraf uygulamasında, yetkilendirme kimliği doğrulanmış bir kimliğin hangi kaynaklara erişebileceğini ve bu kaynaklar üzerinde hangi işlemleri gerçekleştirebileceğini belirler. Uygunsuz veya zayıf yetkilendirme, bilgi ifşasına ve verilerin izinsiz kullanımına neden olur. Bu konuda, Windows Identity Foundation (WIF) ve Microsoft Azure Erişim Denetimi Hizmeti (ACS) gibi Güvenlik Belirteci Hizmeti (STS) kullanılarak talep kullanan ASP.NET web uygulamaları ve hizmetleri için yetkilendirme uygulama yaklaşımları açıklanmaktadır.  
  
## <a name="overview"></a>Genel Bakış  
 İlk sürümünden bu yana, .NET Framework yetkilendirmenin uygulanması için esnek bir mekanizma sunmuştur. Bu mekanizma, iki basit arabirimi tabanlı —**IPrincipal** ve **IIdentity**. In somut uygulamaları **IIdentity** kimliği doğrulanmış bir kullanıcıyı temsil eder. Örneğin, **WindowsIdentity** uygulamasını Active Directory tarafından kimliği doğrulanmış bir kullanıcıyı temsil eder ve **Genericıdentity** özel bir kimliğe doğrulanan bir kullanıcıyı temsil eder kimlik doğrulama işlemi. In somut uygulamaları **IPrincipal** rol deposuna göre rolleri kullanarak izinlerin denetlenmesine yardımcı olur. Örneğin, **WindowsPrincipal** denetler **WindowsIdentity** Active Directory gruplarında üyelik için. Bu onay çağrılarak gerçekleştirilir **IPrincipal** metodunda **IPrincipal** arabirimi. Rollere göre erişim denetimine Rol Tabanlı Erişim Denetimi (RBAC) adı verilir. Daha fazla bilgi için [rol tabanlı erişim denetimi](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_1).  Talepler, benzer, rol tabanlı yetkilendirme mekanizmalarını desteklemek amacıyla roller hakkında bilgi taşımak için kullanılabilir.  
  
 Talepler, rollerin ötesinde daha karmaşık yetkilendirme kararlarının verilmesini sağlamak için de kullanılabilir. Talep kullanıcı - yaş, posta kodu, ayakkabı vb. hakkında neredeyse tüm bilgileri temel alabilir. Rasgele talepleri temel alan erişim denetimi mekanizmasına, beyana dayalı yetkilendirme denir. Daha fazla bilgi için [beyana dayalı yetkilendirme](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_2).  
  
<a name="BKMK_1"></a>   
## <a name="role-based-access-control"></a>Rol Tabanlı Erişim Denetimi  
 RBAC, kullanıcı izinlerinin yönetildiği ve kullanıcı rollerine göre bir uygulama tarafından zorlanan yetkilendirme yaklaşımıdır. Kullanıcının bir eylemi gerçekleştirmesi gereken rolü varsa, erişim verilir; aksi takdirde, erişim engellenir.  
  
### <a name="iprincipalisinrole-method"></a>IPrincipal.IsInRole Yöntemi  
 Talep kullanan uygulamalarda RBAC yaklaşımı uygulamak için kullanma **Isınrole()** yönteminde **IPrincipal** talep kullanmayan uygulamalarda olduğu gibi arabirim. Kullanmanın birkaç yolu vardır **Isınrole()** yöntemi:  
  
- Açıkça çağırma **gt;IPrincipal.ısınrole("Administrator")** . Bu yaklaşımda, sonuç olarak Boole değeri elde edilir. Kendi koşullu deyimlerinizde kullanın. Kodunuzdaki herhangi bir yerde rasgele kullanılabilir.  
  
- Güvenlik talebini kullanma **PrincipalPermission.Demand()** . Bu yaklaşımda, talep karşılanmazsa sonuç olarak bir özel durum elde edilir. Bu, özel durum işleme stratejinizle uyumlu olmalıdır. Özel durumları atma Boolean döndürmekle karşılaştırıldığında performans açısından çok daha pahalı olur. Bu, kodunuzdaki herhangi bir yerde kullanılabilir.  
  
- Bildirim temelli öznitelikleri kullanma **[PrincipalPermission (SecurityAction.Demand, Role = "Administrator")]** . Bu yaklaşıma, yöntemleri donatmak için kullanıldığından bildirim temelli denir. Yöntem uygulamalarının içindeki kod bloklarında kullanılamaz. Talep karşılanmazsa sonuç olarak bir özel durum elde edilir. Özel durum işleme stratejinizle uyumlu olduğundan emin olmanız gerekir.  
  
- URL yetkilendirmesi kullanma  **\<yetkilendirme >** konusundaki **web.config**. Bu yaklaşım, yetkilendirme URL düzeyinde yönetilirken uygundur. Bu, daha önce bahsedilenler arasında en genel düzeydir. Bu yaklaşımın avantajı, değişikliklerin yapılandırma dosyasında yapılması, yani değişiklikten yararlanmak için kodun derlenmesine gerek olmamasıdır.  
  
### <a name="expressing-roles-as-claims"></a>Rolleri Talepler Olarak İfade Etme  
 Zaman **Isınrole()** yöntemi çağrıldığında, geçerli kullanıcının bu role sahip olup olmadığını görmek için yapılan bir denetim yoktur. Talep kullanan uygulamalarda, rol belirteçte kullanılabilir olması gereken bir rol talep türü olarak ifade edilir. Rol talep türü, aşağıdaki URI kullanılarak ifade edilir:  
  
 `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`
  
 Bir belirteci rol talep türüyle zenginleştirmenin birkaç yöntemi vardır:  
  
- **Belirteç verilirken**. Bir kullanıcının kimliği doğrulandığında rol talebi kimlik sağlayıcısı STS veya Windows Azure Access Control Service (ACS) gibi Federasyon sağlayıcısı tarafından verilebilir.  
  
- **Rasgele talepleri ClaimsAuthenticationManager kullanarak talep rolü türüne dönüştürme**. ClaimsAuthenticationManager, WIF'nin bir parçası olarak sunulan bir bileşendir. Uygulama başlattıklarında isteklerin kesilmesini sağlar, belirteçleri denetler ve talepleri ekleyerek, değiştirerek veya kaldırarak dönüştürür. Talepleri dönüştürme için ClaimsAuthenticationManager'ı kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: WIF ve ACS kullanarak talep kullanan ASP.NET uygulamasında uygulama rol tabanlı erişim denetimi (RBAC)](https://go.microsoft.com/fwlink/?LinkID=247445).  
  
- **SamlSecurityTokenRequirement yapılandırma bölümü kullanılarak bir rol türüyle rasgele talep eşleme**— talep dönüştürmenin burada yapılır bildirim temelli bir yaklaşım yalnızca yapılandırmasını ve kodlama kullanarak gereklidir.  
  
<a name="BKMK_2"></a>   
## <a name="claims-based-authorization"></a>Beyana Dayalı Yetkilendirme  
 Beyana dayalı yetkilendirme, erişim verme veya reddetmeye yönelik yetkilendirme kararının, karar verme beyanlarında yer alan verileri kullanan rasgele mantığı temel aldığı bir yaklaşımdır. RBAC söz konusu olduğunda, kullanılan tek talebin rol türü talep olduğunu hatırlayın. Rol türü talep, kullanıcının belirli role ait olup olmadığını denetlemek için kullanıldı. Beyana dayalı yetkilendirme yaklaşımını kullanarak yetkilendirme kararı verme sürecini anlamak için aşağıdaki adımları göz önünde bulundurun:  
  
1. Uygulama, kullanıcının kimliğinin doğrulanmasını gerektiren bir istek alır.  
  
2. WIF, kullanıcıyı kimlik sağlayıcısına yönlendirir, kimliği doğrulandıktan sonra kullanıcıyı temsil eden ve kullanıcı hakkında talepler içeren ilişkili bir güvenlik belirteciyle uygulama isteği yapılır. WIF, bu talepleri kullanıcıyı temsil eden sorumluyla ilişkilendirir.  
  
3. Uygulama, talepleri karar mantığı mekanizmasına geçirir. Bu; bellek içi kod, web hizmeti çağrısı, veritabanı sorgusu, gelişmiş bir kural altyapısı veya ClaimsAuthorizationManager kullanımı olabilir.  
  
4. Karar mekanizması taleplere göre sonucu hesaplar.  
  
5. Sonuç true ise erişim verilir, false ise engellenir. Örneğin, kural kullanıcının 21 yaşında veya daha yaşlı olmasını ve Washington eyaletinde yaşamasını gerektirebilir.  
  
 <xref:System.Security.Claims.ClaimsAuthorizationManager> Uygulamalarınızda beyana dayalı yetkilendirme için karar mantığının alınmasında yararlıdır. ClaimsAuthorizationManager, .NET 4.5'in bir parçası olarak sunulan bir WIF bileşenidir. ClaimsAuthorizationManager, gelen taleplere göre yetkilendirme kararları vermek için gelen istekleri kesmenize ve istediğiniz mantığı uygulamanıza imkan tanır. Bu, yetkilendirme mantığının değiştirilmesi gerektiğinde önemli hale gelir. Bu durumda, ClaimsAuthorizationManager uygulamanın bütünlüğünü etkilemez ve bu nedenle değişikliğin sonucu olarak uygulama hatası oluşma olasılığını azaltır. ClaimsAuthorizationManager, talep tabanlı erişim denetimi uygulamak üzere kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Uygulama yetkilendirme WIF ve ACS kullanarak talep kullanan ASP.NET uygulamasında talep](https://go.microsoft.com/fwlink/?LinkID=247446).
