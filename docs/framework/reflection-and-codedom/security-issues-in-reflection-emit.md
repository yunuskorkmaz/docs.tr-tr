---
title: Yansıma Yaymadaki Güvenlik Sorunları
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- emitting dynamic assemblies, security
- reflection emit, security
- reflection emit, partial trust scenarios
- partial trust,emitting dynamic methods
- anonymously hosted dynamic methods [.NET Framework]
- emitting dynamic assemblies,partial trust scenarios
- dynamic assemblies, security
ms.assetid: 0f8bf8fa-b993-478f-87ab-1a1a7976d298
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57db77b64ddcbe282fed035b52bb122901383ca4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398878"
---
# <a name="security-issues-in-reflection-emit"></a>Yansıma Yaymadaki Güvenlik Sorunları
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Microsoft yayma için üç yol dili (MSIL), her biri kendi güvenlik sorunları Ara sağlar:  
  
-   [Dinamik derlemeler](#Dynamic_Assemblies)  
  
-   [Anonim barındırılan dinamik yöntemler](#Anonymously_Hosted_Dynamic_Methods)  
  
-   [Varolan derlemeler ile ilişkilendirilmiş dinamik yöntemler](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Dinamik kodu oluşturmak şekilde bağımsız olarak, oluşturulan kod yürütme türleri ve oluşturulan kod kullanan yöntemleri tarafından gerekli olan tüm izinleri gerektirir.  
  
> [!NOTE]
>  Kodu yansıtma ve kod yayma için gerekli izinler sürümleri başarılı ile değiştirilmiştir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Bkz: [sürüm bilgilerini](#Version_Information), bu konunun devamındaki.  
  
<a name="Dynamic_Assemblies"></a>   
## <a name="dynamic-assemblies"></a>Dinamik derlemeler  
 Dinamik derlemeleri aşırı kullanarak oluşturulur <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> yöntemi. Bu yöntem çoğu aşırı kullanım dışıdır [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], makine genelinde güvenlik ilkesi eleme nedeniyle. (Bkz [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).) Kalan aşırı güven düzeyi bağımsız olarak herhangi bir kod tarafından çalıştırılabilir. Bu aşırı iki gruba ayrılır: da oluşturulduğunda dinamik derleme uygulamak için öznitelikler listesini belirtin ve değişmeyen. Saydamlık modeli derleme için uygulayarak belirtmezseniz <xref:System.Security.SecurityRulesAttribute> , saydamlık modeli oluşturduğunuzda özniteliği verme derlemeden devralınır.  
  
> [!NOTE]
>  Kullanarak oluşturulduktan sonra dinamik derleme uygulanan öznitelikleri <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> yöntemi, derleme diske kaydedilir ve belleğe yeniden yüklenen kadar etkili olmaz.  
  
 Dinamik derleme kodunda görünür türleri ve diğer derlemelerden üyeleri erişebilir.  
  
> [!NOTE]
>  Dinamik derlemeleri kullanmayın <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> ve <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrakları ortak olmayan türleri ve üyeleri erişmek dinamik yöntemler sağlar.  
  
 Geçici dinamik derlemeleri bellekte oluşturulur ve hiçbir dosya erişim izinlerini gereksinim duydukları şekilde hiçbir zaman diske kaydedilir. Dinamik derleme diske kaydetmek gerektirir <xref:System.Security.Permissions.FileIOPermission> uygun bayraklarla.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Kısmen güvenilen koddan dinamik derlemeleri oluşturma  
 Hangi Internet izinlere sahip bir derleme geçici bir dinamik derleme oluşturabilir ve kendi kod yürütmek koşulları göz önünde bulundurun:  
  
-   Dinamik derleme yalnızca genel türleri ve diğer derlemelerden üyeleri kullanır.  
  
-   Bu türleri ve üyeleri tarafından talep edilen izinler kısmen güvenilen derlemenin grant kümesi dahil edilir.  
  
-   Derleme kaydedilmedi diske.  
  
-   Hata ayıklama simgeleri oluşturulmaz. (`Internet` ve `LocalIntranet` izin kümeleri gerekli izinleri içermez.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>   
## <a name="anonymously-hosted-dynamic-methods"></a>Anonim barındırılan dinamik yöntemler  
 Anonim barındırılan dinamik yöntemler, iki kullanarak oluşturulur <xref:System.Reflection.Emit.DynamicMethod> ilişkili türü veya modül belirtmeyin oluşturucular <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> ve <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>. Bu oluşturucu dinamik yöntemleri bir sistem tarafından sağlanan tam güvenilir, güvenlik saydam derlemede yerleştirin. Bu oluşturucu kullanmak veya kod dinamik yöntemleri yayma için hiçbir izinleri gereklidir.  
  
 Anonim barındırılan dinamik yöntemi oluşturulduğunda, bunun yerine, çağrı yığını yakalanır. Yöntemin oluşturulduğunda güvenlik taleplerini yakalanan çağrı yığını karşı yapılır.  
  
> [!NOTE]
>  Kavramsal olarak, taleplerin yöntemi oluşturma sırasında yapılır. Diğer bir deyişle, her MSIL yönergesi yayılan gibi taleplerini yapılamadı. Geçerli uygulama, ne zaman tüm taleplerin yapılan <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> yöntemi çağrıldığında veya ne zaman tam zamanında (JIT) derleyici çağrılır, yöntem çağırma olmadan çağrılırsa <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  
  
 Uygulama etki alanı izin veriliyorsa, anonim barındırılan dinamik yöntemler aşağıdaki kısıtlama tabi JIT görünürlük denetimleri atlayabilirsiniz: ortak olmayan türleri ve üyeleri bir anonim barındırılan dinamik yöntemi tarafından erişilen, grant ayarlar derlemelerde olmalıdır eşit ya da bir veri alt kümesini, verme çağrı yığını grant kümesi var. JIT görünürlük atlamak için kısıtlı özelliği denetler etkin uygulama etki alanı verirse <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağı.  
  
-   Hiçbir izinler yönteminizi yalnızca genel türleri ve üyeleri kullanıyorsa, oluşturma sırasında gereklidir.  
  
-   JIT görünürlük atlanır denetler belirtirseniz, yöntem oluşturulduğunda gerçekleştiren talep içeren <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağı ve erişiliyor ortak olmayan üyeyi içeren derlemenin grant kümesi.  
  
 Özel üye grant kümesi dikkate alınır çünkü verildi kod kısmen güvenilir <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> kendi ayrıcalıklarını güvenilen derlemelerin ortak olmayan üyeler yürüterek yükseltme yapamazsınız.  
  
 Olarak herhangi diğer verilmiş koduyla dinamik yöntemini yürütmenin tüm izinler dinamik bir yöntem yöntemler tarafından talep gerektirir.  
  
 Anonim barındırılan dinamik yöntemler barındıran sistem derlemesi kullanan <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> önce .NET Framework içinde kullanılan saydamlık model saydamlık modeli [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
 Daha fazla bilgi için bkz: <xref:System.Reflection.Emit.DynamicMethod> sınıfı.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Barındırılan dinamik yöntemler kısmen güvenilen koddan anonim olarak oluşturma  
 Internet izinlere sahip bir derleme üretme anonim barındırılan dinamik yöntemi ve yürütebilirsiniz koşulları göz önünde bulundurun:  
  
-   Yalnızca genel türleri ve üyeleri dinamik yöntemi kullanır. Verme kümesi içeriyorsa <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, ortak olmayan türleri kullanabilirsiniz ve, grant ayarlamak derleme üyeleri olduğundan eşit ya da bir alt kümesini, verme derlemenin grant kümesi.  
  
-   Tüm türleri ve dinamik yöntemi tarafından kullanılan üyeleri gerektirdiği izinler kısmen güvenilen derlemenin grant kümesi dahil edilir.  
  
> [!NOTE]
>  Dinamik yöntemler hata ayıklama simgeleri desteklemez.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>   
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Varolan derlemeler ile ilişkilendirilmiş dinamik yöntemler  
 Dinamik bir yöntem türü veya mevcut bir derlemede modülü ilişkilendirmek için herhangi bir kullanmak <xref:System.Reflection.Emit.DynamicMethod> ilişkili türü veya modülü belirtin oluşturucular. Dinamik bir yöntem varolan türüyle ilişkilendirme çünkü bu oluşturucular aramak için gerekli izinleri farklılık veya ortak olmayan türleri ve üyeleri için modülü dinamik yöntemi erişim sağlar:  
  
-   Türü ile ilişkili olmayan dinamik bir yöntemle bile özel üyeler, bu türdeki tüm üyelerin erişimi ve ilişkili türü içeren tüm iç türleri ve üyeleri derlemesindeki.  
  
-   Bir modülü ile ilişkili dinamik bir yöntem erişimi olan `internal` türleri ve üyeleri (`Friend` Visual Basic'te `assembly` ortak dil çalışma zamanı meta verilerde) modülünde.  
  
 Ayrıca, görünürlük Atla yeteneği JIT Derleyici denetleyeceğini belirtir bir oluşturucu kullanabilirsiniz. Bunun yapılması, dinamik yöntemi tüm türleri ve üyeleri erişim düzeyi bağımsız olarak tüm derlemelerde erişmenizi sağlar.  
  
 Yapıcı tarafından talep edilen izinler bağlıdır dinamik yönteminizi vermek karar ne kadar erişimi:  
  
-   Yalnızca genel türleri ve üyeleri yönteminizi kullanıyorsa ve kendi türü veya kendi modülü ile ilişkilendirmek, hiçbir izinleri gereklidir.  
  
-   JIT görünürlük denetimleri atlanacağını belirtirseniz, Oluşturucusu talep <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağı.  
  
-   Dinamik yöntemi başka bir türü ile ilişkilendirirseniz, kendi derlemesindeki başka bir tür Oluşturucu talep bile <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağı ve <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> bayrağı.  
  
-   Bir tür veya başka bir derlemede modülüyle dinamik yöntemi ilişkilendirirseniz Oluşturucusu iki şey talep: <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağı ve başka bir modül içeren derlemenin grant kümesi. Diğer bir deyişle, çağrı yığını tüm izinleri hedef modülü grant kümesini içermelidir artı <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
    > [!NOTE]
    >  Hedef talep kümesi sağlıyorsa geriye dönük uyumluluk için artı <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> başarısız olursa Oluşturucusu taleplerini <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> bayrağı.  
  
 Bu listedeki öğeler verme derleme verme kümesi bakımından açıklanan rağmen taleplerini uygulama etki alanı sınırını da dahil olmak üzere tam çağrı yığını karşı yapılır unutmayın.  
  
 Daha fazla bilgi için bkz: <xref:System.Reflection.Emit.DynamicMethod> sınıfı.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Kısmen güvenilen koddan dinamik yöntemleri oluşturma  
  
> [!NOTE]
>  Kısmen güvenilen koddan dinamik yöntemleri oluşturmak için önerilen yöntem kullanmaktır [anonim barındırılan dinamik yöntemler](#Anonymously_Hosted_Dynamic_Methods).  
  
 Internet izinlere sahip bir derleme üretme dinamik yöntemi ve yürütebilirsiniz koşulları göz önünde bulundurun:  
  
-   Dinamik yöntemi modülü veya onu yayar türü ile ilişkili değil veya kendi verme kümesi içeren <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> ve, grant bütünleştirilmiş modülünde ilişkilendirildiği eşit ya da bir alt kümesini, verme derlemenin grant kümesi kümesidir.  
  
-   Yalnızca genel türleri ve üyeleri dinamik yöntemi kullanır. Verme kümesi içeriyorsa <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> ve, grant bütünleştirilmiş modülünde ilişkilendirildiği kümesidir eşit ya da bir alt kümesini, verme derlemenin grant kümesi, türleri ve işaretlenen üyelerin kullanabilirsiniz `internal` (`Friend` Visual Basic'te `assembly`ortak dil çalışma zamanı meta verilerde) ilişkili modülünde.  
  
-   Tüm türleri tarafından talep edilen izinler ve dinamik yöntemi tarafından kullanılan üye kısmen güvenilen derlemenin grant kümesi dahil edilir.  
  
-   Dinamik yöntemi JIT görünürlük denetimleri atlamaz.  
  
> [!NOTE]
>  Dinamik yöntemler hata ayıklama simgeleri desteklemez.  
  
<a name="Version_Information"></a>   
## <a name="version-information"></a>Sürüm Bilgileri  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], makine genelinde güvenlik ilkesi ortadan ve güvenlik saydamlık varsayılan zorlama mekanizmasının haline gelir. Bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
 İle başlayarak [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> bayrağı gereklidir artık dinamik derlemeler ve dinamik yöntemleri yayma. Bu bayrak tüm önceki sürümlerde gerekli [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> bayrak varsayılan olarak dahil `FullTrust` ve `LocalIntranet` adlandırılmış izin ayarlar, ancak içinde değil `Internet` izin kümesi. Bu nedenle,'ın önceki sürümlerinde [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], yalnızca yürütür varsa, Internet izinleri olan bir kitaplık kullanılabilir bir <xref:System.Security.PermissionSet.Assert%2A> için <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Kodlama hataları güvenlik açıklarını neden olabilir çünkü böyle kitaplıklarının dikkatli güvenlik incelemesi gerektirir. [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] Kısmi güven senaryolarında kod oluşturma için tüm güvenlik taleplerini veren kendiliğinden ayrıcalıklı bir işlem değil olmadan yayınlaması için kod sağlar. Diğer bir deyişle, oluşturulan kod bunu yayar derleme'den daha fazla hiçbir izni yoktur. Güvenliği saydam kod yayma ve assert ihtiyacını ortadan kaldırır kitaplıkları böylece <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, güvenli bir kitaplık yazma görevini basitleştirir.  
  
 Ayrıca, [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] tanıtır <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> ortak olmayan türleri ve üye kısmen güvenilen dinamik yöntemleri erişmek için bayrak. ' In önceki sürümlerini [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] gerektiren <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrak ortak olmayan türleri ve üyeleri erişmek için dinamik yöntemleri; Bu kısmen güvenilen kod hiçbir zaman verilmelidir izni.  
  
 Son olarak, [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] anonim olarak barındırılan yöntemleri sunar.  
  
### <a name="obtaining-information-on-types-and-members"></a>Türleri ve üyeleri hakkında bilgi edinme  
 İle başlayarak [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], ortak olmayan türleri ve üyeleri hakkında bilgi edinmek için hiçbir izinleri gereklidir. Yansıma dinamik yöntemleri yayma için gereken bilgileri elde etmek için kullanılır. Örneğin, <xref:System.Reflection.MethodInfo> nesneleri yöntem çağrılarını yaymak üzere kullanılır. ' In önceki sürümlerini [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] gerektiren <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> bayrağı. Daha fazla bilgi için bkz: [yansımayla ilgili güvenlik konuları](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yansımayla İlgili Güvenlik Konuları](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)  
 [Dinamik Yöntemleri ve Derlemeleri Yayma](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)
