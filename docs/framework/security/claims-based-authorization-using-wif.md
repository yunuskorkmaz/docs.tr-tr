---
title: WIF Kullanarak Talep Tabanlı Yetkilendirme
ms.date: 03/30/2017
ms.assetid: e24000a3-8fd8-4c0e-bdf0-39882cc0f6d8
author: BrucePerlerMS
ms.openlocfilehash: ebf4c28bd2a46c21535b596af22d1fa420d20e71
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045496"
---
# <a name="claims-based-authorization-using-wif"></a>WIF Kullanarak Talep Tabanlı Yetkilendirme
Bağlı taraf uygulamasında, yetkilendirme kimliği doğrulanmış bir kimliğin hangi kaynaklara erişebileceğini ve bu kaynaklar üzerinde hangi işlemleri gerçekleştirebileceğini belirler. Uygunsuz veya zayıf yetkilendirme, bilgi ifşasına ve verilerin izinsiz kullanımına neden olur. Bu konuda, Windows Identity Foundation (WIF) ve Microsoft Azure Erişim Denetimi Hizmeti (ACS) gibi Güvenlik Belirteci Hizmeti (STS) kullanılarak talep kullanan ASP.NET web uygulamaları ve hizmetleri için yetkilendirme uygulama yaklaşımları açıklanmaktadır.  
  
## <a name="overview"></a>Genel Bakış  
 İlk sürümünden bu yana, .NET Framework yetkilendirmenin uygulanması için esnek bir mekanizma sunmuştur. Bu mekanizma,**IPrincipal** ve **IIdentity**olmak üzere iki basit arabirime dayanır. **IIdentity** somut uygulamaları kimliği doğrulanmış bir kullanıcıyı temsil eder. Örneğin, **WindowsIdentity** uygulama Active Directory tarafından kimlik doğrulayan bir kullanıcıyı temsil eder ve **GenericIdentity** , kimliği özel bir kimlik doğrulama işlemi aracılığıyla doğrulanan bir kullanıcıyı temsil eder. **IPrincipal** 'un somut uygulamaları, rol deposuna bağlı olarak rolleri kullanarak izinleri denetlemeye yardımcı olur. Örneğin, **WindowsPrincipal** Active Directory gruplardaki üyelik Için **WindowsIdentity** denetler. Bu denetim, **IPrincipal** arabiriminde **IsInRole** yöntemi çağırarak gerçekleştirilir. Rollere göre erişim denetimine Rol Tabanlı Erişim Denetimi (RBAC) adı verilir. Daha fazla bilgi için bkz. [rol tabanlı Access Control](claims-based-authorization-using-wif.md#BKMK_1).  Talepler, benzer, rol tabanlı yetkilendirme mekanizmalarını desteklemek amacıyla roller hakkında bilgi taşımak için kullanılabilir.  
  
 Talepler, rollerin ötesinde daha karmaşık yetkilendirme kararlarının verilmesini sağlamak için de kullanılabilir. Talepler, Kullanıcı yaşı, posta kodu, showe boyutu vb. hakkında neredeyse her türlü bilgiyi temel alabilir. Rastgele talepler temelli bir erişim denetimi mekanizmasına, talep tabanlı yetkilendirme denir. Daha fazla bilgi için bkz. [talep tabanlı yetkilendirme](claims-based-authorization-using-wif.md#BKMK_2).  
  
<a name="BKMK_1"></a>   
## <a name="role-based-access-control"></a>Rol Tabanlı Erişim Denetimi  
 RBAC, kullanıcı izinlerinin yönetildiği ve kullanıcı rollerine göre bir uygulama tarafından zorlanan yetkilendirme yaklaşımıdır. Kullanıcının bir eylemi gerçekleştirmesi gereken rolü varsa, erişim verilir; aksi takdirde, erişim engellenir.  
  
### <a name="iprincipalisinrole-method"></a>IPrincipal.IsInRole Yöntemi  
 Talep kullanan uygulamalarda RBAC yaklaşımını uygulamak için, **IPrincipal** arabirimindeki **ıınrole ()** yöntemini, talep kullanmayan uygulamalarda olduğu gibi kullanın. **Iınrole ()** yöntemini kullanmanın birkaç yolu vardır:  
  
- **IPrincipal. IsInRole ("Administrator")** açık olarak çağrılıyor. Bu yaklaşımda, sonuç olarak Boole değeri elde edilir. Kendi koşullu deyimlerinizde kullanın. Kodunuzdaki herhangi bir yerde rasgele kullanılabilir.  
  
- Güvenlik talebi **PrincipalPermission. Demand ()** kullanılıyor. Bu yaklaşımda, talep karşılanmazsa sonuç olarak bir özel durum elde edilir. Bu, özel durum işleme stratejinizle uyumlu olmalıdır. Özel durum atma, Boolean döndürme ile karşılaştırıldığında performans perspektifinden çok daha pahalıdır. Bu, kodunuzdaki herhangi bir yerde kullanılabilir.  
  
- Bildirim temelli öznitelikleri kullanma **[PrincipalPermission (SecurityAction. Demand, role = "Administrator")]** . Bu yaklaşıma, yöntemleri donatmak için kullanıldığından bildirim temelli denir. Yöntem uygulamalarının içindeki kod bloklarında kullanılamaz. Talep karşılanmazsa sonuç olarak bir özel durum elde edilir. Özel durum işleme stratejinizle uyumlu olduğundan emin olmanız gerekir.  
  
- **Web. config**'deki  **\<yetkilendirme >** bölümünü kullanarak URL yetkilendirmesini kullanma. Bu yaklaşım, yetkilendirme URL düzeyinde yönetilirken uygundur. Bu, daha önce bahsedilenler arasında en genel düzeydir. Bu yaklaşımın avantajı, değişikliklerin yapılandırma dosyasında yapılması, yani değişiklikten yararlanmak için kodun derlenmesine gerek olmamasıdır.  
  
### <a name="expressing-roles-as-claims"></a>Rolleri Talepler Olarak İfade Etme  
 **IsInRole ()** yöntemi çağrıldığında, geçerli kullanıcının bu role sahip olup olmadığını görmek için bir denetim yapılır. Talep kullanan uygulamalarda, rol belirteçte kullanılabilir olması gereken bir rol talep türü olarak ifade edilir. Rol talep türü, aşağıdaki URI kullanılarak ifade edilir:  
  
 `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`
  
 Bir belirteci rol talep türüyle zenginleştirmenin birkaç yöntemi vardır:  
  
- **Belirteç verme sırasında**. Bir kullanıcının kimliği doğrulandığında, rol talebi kimlik sağlayıcısı STS tarafından veya Microsoft Azure Access Control Service (ACS) gibi bir Federasyon sağlayıcısı tarafından verilebilir.  
  
- **ClaimsAuthenticationManager kullanarak rastgele talepleri talep rolü türüne dönüştürme**. ClaimsAuthenticationManager, WIF'nin bir parçası olarak sunulan bir bileşendir. Uygulama başlattıklarında isteklerin kesilmesini sağlar, belirteçleri denetler ve talepleri ekleyerek, değiştirerek veya kaldırarak dönüştürür. Talepleri dönüştürmek için ClaimsAuthenticationManager kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: WıF ve ACS](https://go.microsoft.com/fwlink/?LinkID=247445)kullanarak talep kullanan bir ASP.NET uygulamasında rol tabanlı Access Control (RBAC) uygulayın.  
  
- **Rastgele talepleri, samlSecurityTokenRequirement yapılandırma bölümünü kullanarak bir rol türüyle eşleme**— talep dönüşümünün yalnızca yapılandırma kullanılarak yapıldığı ve kodlama gerekmediği bildirime dayalı bir yaklaşım.  
  
<a name="BKMK_2"></a>   
## <a name="claims-based-authorization"></a>Beyana Dayalı Yetkilendirme  
 Beyana dayalı yetkilendirme, erişim verme veya reddetmeye yönelik yetkilendirme kararının, karar verme beyanlarında yer alan verileri kullanan rasgele mantığı temel aldığı bir yaklaşımdır. RBAC söz konusu olduğunda, kullanılan tek talebin rol türü talep olduğunu hatırlayın. Rol türü talep, kullanıcının belirli role ait olup olmadığını denetlemek için kullanıldı. Beyana dayalı yetkilendirme yaklaşımını kullanarak yetkilendirme kararı verme sürecini anlamak için aşağıdaki adımları göz önünde bulundurun:  
  
1. Uygulama, kullanıcının kimliğinin doğrulanmasını gerektiren bir istek alır.  
  
2. WIF, kullanıcıyı kimlik sağlayıcısına yönlendirir, kimliği doğrulandıktan sonra kullanıcıyı temsil eden ve kullanıcı hakkında talepler içeren ilişkili bir güvenlik belirteciyle uygulama isteği yapılır. WIF, bu talepleri kullanıcıyı temsil eden sorumluyla ilişkilendirir.  
  
3. Uygulama, talepleri karar mantığı mekanizmasına geçirir. Bu; bellek içi kod, web hizmeti çağrısı, veritabanı sorgusu, gelişmiş bir kural altyapısı veya ClaimsAuthorizationManager kullanımı olabilir.  
  
4. Karar mekanizması taleplere göre sonucu hesaplar.  
  
5. Sonuç true ise erişim verilir, false ise engellenir. Örneğin, kural kullanıcının 21 yaşında veya daha yaşlı olmasını ve Washington eyaletinde yaşamasını gerektirebilir.  
  
 <xref:System.Security.Claims.ClaimsAuthorizationManager>, uygulamalarınızda talep tabanlı yetkilendirme için karar mantığını temel almak için yararlıdır. ClaimsAuthorizationManager, .NET 4.5'in bir parçası olarak sunulan bir WIF bileşenidir. ClaimsAuthorizationManager, gelen taleplere göre yetkilendirme kararları vermek için gelen istekleri kesmenize ve istediğiniz mantığı uygulamanıza imkan tanır. Bu, yetkilendirme mantığının değiştirilmesi gerektiğinde önemli hale gelir. Bu durumda, ClaimsAuthorizationManager uygulamanın bütünlüğünü etkilemez ve bu nedenle değişikliğin sonucu olarak uygulama hatası oluşma olasılığını azaltır. Talep tabanlı erişim denetimi uygulamak için ClaimsAuthorizationManager 'ın nasıl kullanılacağı hakkında daha fazla bilgi edinmek için bkz [. nasıl yapılır: Bir talep kullanan ASP.NET uygulamasında WıF ve ACS](https://go.microsoft.com/fwlink/?LinkID=247446)kullanarak talep yetkilendirmesi uygulayın.
