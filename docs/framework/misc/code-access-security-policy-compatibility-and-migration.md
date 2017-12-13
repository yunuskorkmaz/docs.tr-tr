---
title: "Kod Erişimi Güvenliği İlkesi Uyumluluğu ve Geçiş"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- policy migration, compatibility
- CLR poliicy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11c64d3ece454e95adfc41c7d89913e9ce7363dc
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2017
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Kod Erişimi Güvenliği İlkesi Uyumluluğu ve Geçiş
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Kod erişim güvenliği (CAS) ilkesi kısmı'te eski haline getirilmiştir [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Geçersiz ilke türleri ve üyeleri çağırırsanız sonuç olarak, derleme uyarıları ve çalışma zamanı özel durumları karşılaşabileceğiniz [açıkça](#explicit_use) veya [örtük olarak](#implicit_use) (aracılığıyla, diğer türleri ve üyeleri).  
  
 Ya da uyarıları ve hataları önleyebilirsiniz:  
  
-   [Geçiş](#migration) için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] eski çağrıları donanımlarının.  
  
     \-veya -  
  
-   Kullanarak [< NetFx40_LegacySecurityPolicy > yapılandırma öğesi](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) eski CA ilke davranışı kabul etmek için.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Açık kullanın](#explicit_use)  
  
-   [Örtük kullanın](#implicit_use)  
  
-   [Hatalar ve uyarılar](#errors_and_warnings)  
  
-   [Geçiş: Artık kullanılmayan çağrıları değiştirme](#migration)  
  
-   [Uyumluluğu: CA ilke eski seçeneği kullanma](#compatibility)  
  
<a name="explicit_use"></a>   
## <a name="explicit-use"></a>Açık kullanın  
 Güvenlik ilkesini değiştirmek veya korumalı alan için CA ilke iste doğrudan üyeleri eskidir ve hataları varsayılan olarak oluşturur.  
  
 Bu örnekleri şunlardır:  
  
-   <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>  
  
<a name="implicit_use"></a>   
## <a name="implicit-use"></a>Örtük kullanın  
 Yükleme birkaç derleme ürettiği hataları örtük kendi CA ilke kullanımı nedeniyle overloads. Bu aşırı ele bir <xref:System.Security.Policy.Evidence> CAS ilkesini çözümlemek ve izin sağlamak için kullanılan parametre kümesi bir derlemenin verin.  
  
 İşte bazı örnekler. Uygulamanız artık kullanılmayan aşırı dosyalardır <xref:System.Security.Policy.Evidence> bir parametre olarak:  
  
-   <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
<a name="errors_and_warnings"></a>   
## <a name="errors-and-warnings"></a>Hatalar ve uyarılar  
 Bunların ne zaman kullanıldığını eski türler ve üyeleri aşağıdaki hata iletilerinden üretir. Unutmayın <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> kendisini türü artık kullanılmayan değil.  
  
 Derleme zamanı Uyarı:  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`  
  
 Çalışma zamanı özel durum:  
  
 <xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`  
  
<a name="migration"></a>   
## <a name="migration-replacement-for-obsolete-calls"></a>Geçiş: Artık kullanılmayan çağrıları değiştirme  
  
### <a name="determining-an-assemblys-trust-level"></a>Bir derlemenin güven düzeyini belirleme  
 CA ilke genellikle bir derlemenin belirlemek için kullanılan veya uygulama etki alanının izin kümesi vermek veya güven düzeyi. [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Güvenlik ilkesi çözmek zorunda kalmazsınız aşağıdaki yararlı özellikleri sunar:  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
### <a name="application-domain-sandboxing"></a>Uygulama etki alanı korumalı alan  
 <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Yöntemdir genellikle uygulama etki alanı derlemelerde korumalı alan için kullanılır. [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Kullanmak zorunda değilsiniz üyeleri ortaya koyar <xref:System.Security.Policy.PolicyLevel> bu amaç için. Daha fazla bilgi için bkz: [nasıl yapılır: çalıştırma kısmen güvenilen kod içinde bir korumalı alan](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Güvenilir kod kısmen güvenli veya makul izni için Ayarla belirleme  
 Ana bilgisayarlar genellikle barındırılan korumalı alan kodu için uygun izinler belirlemeniz gerekir. Önce [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], CAS ilkesini sağlanan ile bunu yapmanın bir yolu <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> yöntemi. Bir yedek olarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] sağlar <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> yöntemi için sağlanan kanıt ayarlamak güvenli, standart bir izin verir.  
  
### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Korumalı alan olmayan senaryolar: Derleme yüklerini aşırı yüklemeleri  
 Aksi takdirde derleme korumalı alan yerine, kullanılabilir değil parametrelerini kullanmak için bir derleme yük aşırı kullanmanın nedeni olabilir. İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], gerektirmez derleme yük overloads bir <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> nesnesi bir bu gibi bir durumda parametresi olarak <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, bu senaryoyu.  
  
 Korumalı alan için bir derleme istiyorsanız kullanın <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> aşırı yükleme.  
  
<a name="compatibility"></a>   
## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Uyumluluğu: CA ilke eski seçeneği kullanma  
 [< NetFx40_LegacySecurityPolicy > yapılandırma öğesi](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) bir işlem veya kitaplık eski CAS ilkesini kullandığını belirtmenize olanak sağlar. Bu öğe etkinleştirdiğinizde, ilke ve kanıt aşırı framework'ün önceki sürümlerinde olduğu gibi çalışır.  
  
> [!NOTE]
>  Bir çalışma zamanı sürümü için CAS ilkesini değiştirme başka bir sürümü CAS ilkesini etkilemesini CA ilke davranışı bir çalışma zamanı sürümü temelinde belirtilir.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: korumalı alanda kısmen güvenilen kodu çalıştırma](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [Güvenli kodlama yönergeleri](../../standard/security/secure-coding-guidelines.md)
