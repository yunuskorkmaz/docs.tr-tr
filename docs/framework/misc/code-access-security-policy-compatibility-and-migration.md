---
title: Kod Erişim Güvenlik İlkesi Uyumluluğu ve Geçiş
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 163ed8d00e8f0f886481dbaca956bb633a625871
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487977"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Kod Erişim Güvenlik İlkesi Uyumluluğu ve Geçiş

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Kod erişimi güvenliği (CAS) ilkesi kısmı .NET Framework 4'te eski haline getirilmiştir. Geçersiz ilke türleri ve üyeleri çağırırsanız sonuç olarak, derleme uyarıları ve çalışma zamanı özel durumları karşılaşabileceğiniz [açıkça](#explicit_use) veya [örtük olarak](#implicit_use) (aracılığıyla, diğer türler ve Üyeler).

Ya da uyarıları ve hataları önleyebilirsiniz:

- [Geçiş](#migration) eski çağrıları için .NET Framework 4 değiştirmeler için.

   \- veya -

- Kullanarak [< NetFx40_LegacySecurityPolicy > yapılandırma öğesi](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) eski CAS ilkesi davranışı kabul etme.

Bu konu aşağıdaki bölümleri içermektedir:

- [Açık kullanın](#explicit_use)

- [Örtük kullanım](#implicit_use)

- [Hatalar ve Uyarılar](#errors_and_warnings)

- [Geçişi: Eski çağrıları için değiştirme](#migration)

- [Uyumluluk: Eski CAS ilkesini seçeneğiyle](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a>Açık kullanın

Korumalı alan için CAS ilkesini doğrudan güvenlik ilkesini değiştirmek veya üyeleri artık kullanılmayan ve varsayılan olarak hataya neden.

Bu örnekleri şunlardır:

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a>Örtük kullanım

Birkaç derleme yükleme üretim hataları örtük kendi CAS ilkesini kullanımı nedeniyle aşırı. Bu aşırı yüklemeler ele bir <xref:System.Security.Policy.Evidence> CAS ilkesini çözmek ve izin sağlamak için kullanılan parametre kümesi için bir derleme verin.

Bazı örnekler aşağıda verilmiştir. Alan geçersiz aşırı olanlardır <xref:System.Security.Policy.Evidence> bir parametre olarak:

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a>Hatalar ve Uyarılar

Kullanıldıklarında aşağıdaki hata iletilerinden artık kullanılmayan türler ve üyeler oluşturur. Unutmayın <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> türün kendisine eski değil.

Derleme zamanı uyarısı:

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

Çalışma zamanı özel durum:

<xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a>Geçişi: Eski çağrıları için değiştirme

### <a name="determining-an-assemblys-trust-level"></a>Bir derlemenin güven düzeyine belirleme

CAS ilkesini genellikle bir derlemenin belirlemek için kullanılan veya uygulama etki alanının izin kümesi vermek ya da güven düzeyi. .NET Framework 4 güvenlik ilkesi çözmek zorunda değildir aşağıdaki kullanışlı özellikler sunar:

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a>Uygulama etki alanı korumalı alana alma

<xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Yöntemi, genellikle uygulama etki alanında derlemeleri korumalı alana alma için kullanılır. .NET Framework 4 kullanmak için olmayan üyeleri ortaya koyar <xref:System.Security.Policy.PolicyLevel> bu amaç için. Daha fazla bilgi için [nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Kısmen güvenli ya da makul bir izin için kümesinin belirleme güvenilen kod

Ana bilgisayar genellikle barındırılan bir korumalı alana alma kodu için uygun izinler belirlemeniz gerekir. Önce .NET Framework 4, CAS ilkesini ile bunu yapmanın bir yolu sağlanan <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> yöntemi. Bunun yerine, .NET Framework 4 sağlar <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> yöntemi için sağlanan kanıt kümesi güvenli, standart bir izin verir.

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Korumalı alana alma olmayan senaryolar: Derleme yüklerini için aşırı yüklemeleri

Aksi takdirde derleme korumalı alana alma yerine mevcut olmayan parametreleri kullanmak bir derleme yük aşırı kullanılmasının nedeni olabilir. .NET Framework 4 ile başlayarak, derleme yükleme gerektirmez aşırı bir <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> bir bu gibi bir durumda parametre olarak nesne <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, bu senaryoyu etkinleştirmek.

Korumalı alan için bir derleme istiyorsanız kullanın <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> aşırı yükleme.

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Uyumluluk: Eski CAS ilkesini seçeneğiyle

[< NetFx40_LegacySecurityPolicy > yapılandırma öğesi](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) bir işlem veya kitaplık eski CAS ilkesini kullanan belirtmenize olanak tanır. Bu öğe etkinleştirdiğinizde, ilke ve kanıt aşırı framework'ün önceki sürümlerinde olduğu gibi çalışır.

> [!NOTE]
> Bir çalışma zamanı sürümü için CAS ilkesini değiştirme başka bir sürümü CAS ilkesini etkilemez bu nedenle CA ilkesi davranışını bir çalışma zamanı sürümü temelinde belirtilir.

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
