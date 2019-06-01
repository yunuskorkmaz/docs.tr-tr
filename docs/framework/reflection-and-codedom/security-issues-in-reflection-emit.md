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
ms.openlocfilehash: 5ca4a087b60e6cb857ec78273dad099e5e5da07a
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457310"
---
# <a name="security-issues-in-reflection-emit"></a>Yansıma Yaymadaki Güvenlik Sorunları
.NET Framework, Microsoft Ara dilini (MSIL), her biri kendi güvenlik sorunları yaymak için üç yol sunar:  
  
- [Dinamik derlemeler](#Dynamic_Assemblies)  
  
- [Anonim olarak barındırılan dinamik yöntemler](#Anonymously_Hosted_Dynamic_Methods)  
  
- [Dinamik yöntemler varolan derlemeleri ile ilişkili](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Dinamik kod üretebilirsiniz yönteminden bağımsız olarak, oluşturulan kod yürütme, türleri ve yöntemleri oluşturulan kod tarafından gereken tüm izinleri gerektirir.  
  
> [!NOTE]
>  Kodu yansıtarak ve kod yayan için gerekli izinler, .NET Framework sürümleri başarılı ile değişti. Bkz: [sürüm bilgisi](#Version_Information), bu konunun devamındaki.  
  
<a name="Dynamic_Assemblies"></a>   
## <a name="dynamic-assemblies"></a>Dinamik derlemeler  
 Dinamik derlemeler aşırı yüklemeleri kullanılarak oluşturulan <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> yöntemi. Bu yöntemin çoğu aşırı kullanım dışı olan [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], makine genelindeki güvenlik ilkesi saydamlığından nedeniyle. (Bkz [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).) Kalan aşırı güven düzeyi bağımsız olarak herhangi bir kod tarafından yürütülebilir. Bu aşırı yüklemeler iki gruba ayrılır: Bu oluşturulduğunda dinamik derlemeye uygulanacak özniteliklerin listesini belirtin ve değişmeyen. Saydamlık modeli derleme için uygulayarak belirtmezseniz <xref:System.Security.SecurityRulesAttribute> özniteliği, saydamlık modeli oluşturduğunuzda, yayan derlemenin devralınır.  
  
> [!NOTE]
>  Kullanarak oluşturulduktan sonra dinamik derlemeye uygulanan öznitelikleri <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> yöntemi, derleme diske kaydedilebilir ve yeniden belleğe yüklenen kadar geçerlilik kazanmaz.  
  
 Dinamik bir derleme kodunda görünebilir türler ve üyeler diğer derlemelerdeki erişebilirsiniz.  
  
> [!NOTE]
>  Dinamik derlemeler kullanmayın <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> ve <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> ortak olmayan türler ve üyeler erişmek dinamik yöntemler sağlayan bayrak.  
  
 Geçici dinamik derlemeler bellekte oluşturulur ve bunlar hiçbir dosya erişim izinlerini gerektirir böylece hiçbir zaman diske kaydedildi. Dinamik bir derleme diske kaydedilirken gerektirir <xref:System.Security.Permissions.FileIOPermission> uygun bayrağı ile.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Kısmen güvenilen koddan dinamik derlemeler oluşturma  
 Internet izinlerine sahip bir derleme geçici dinamik derleme oluşturmak ve, kod yürütmesine koşulları göz önünde bulundurun:  
  
- Dinamik derlemenin yalnızca genel türleri ve üyeleri diğer derlemelerin kullanır.  
  
- Bu türler ve üyeler tarafından talep edilen izinler kısmen güvenilen bir derlemede izin kümesi dahil edilir.  
  
- Derleme kaydedilmedi diske.  
  
- Hata ayıklama sembolleri oluşturulmaz. (`Internet` ve `LocalIntranet` izin kümeleri gerekli izinleri içermez.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>   
## <a name="anonymously-hosted-dynamic-methods"></a>Anonim barındırılan dinamik metotlar  
 Anonim olarak barındırılan dinamik yöntemler iki kullanılarak oluşturulan <xref:System.Reflection.Emit.DynamicMethod> bir ilişkili typ nebo modul, belirtmeyin oluşturucular <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> ve <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>. Bu oluşturucu, sistem tarafından sağlanan, tam olarak güvenilir, güvenlik açısından saydam bir derlemede dinamik yöntemler yerleştirin. İzin yok, bu oluşturucular kullanın veya dinamik yöntemleri için kod yaymak için gereklidir.  
  
 Bunun yerine, çağrı yığını anonim olarak barındırılan bir dinamik yöntem oluşturulduğunda dahil edilir. Yöntem oluşturulduğunda, güvenlik taleplerini yakalanan çağrı yığını karşı yapılır.  
  
> [!NOTE]
>  Kavramsal olarak, talepleri yönteminin yapılandırılması sırasında yapılır. Diğer bir deyişle, her MSIL yönergesi yayılan gibi taleplerini yapılamadı. Geçerli uygulamada ne zaman tüm taleplerin yapılan <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> yöntemi çağrıldığında veya ne zaman just-in-time (JIT) derleyici çağrılır, yöntemi çağırmadan olmadan çağırdığınız <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  
  
 Uygulama etki alanı izin veriliyorsa, anonim olarak barındırılan dinamik yöntemlerin JIT görünürlük denetimlerini aşağıdaki kısıtlama tabi atlayabilirsiniz: Ortak olmayan türler ve üyeler tarafından anonim olarak barındırılan dinamik bir yöntem erişilen derlemelerde, izin kümeleri eşit olan veya kümelerine, yayan çağrı yığınını izin kümesi olması gerekir. Bu kısıtlı özelliği JIT görünürlük atlamak için denetler etkin uygulama etki alanı verirse <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağı.  
  
- İzin yok, yöntemi yalnızca genel türleri ve üyeleri kullanıyorsa, yapım sırasında gereklidir.  
  
- Atlanacak JIT görünürlük denetimleri belirtirseniz, yöntem oluşturulduğunda gerçekleştiren talep içeren <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağı ve izin kümesi erişiliyor ortak olmayan üyeyi içeren derleme.  
  
 Ortak olmayan üyeye izin kümesi dikkate alınır olduğundan, verilmiş kod kısmen güvenilen <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> güvenilir derlemelerinin ortak olmayan üyeler yürüterek kendi ayrıcalıklarını yükseltme yapamazsınız.  
  
 Olarak herhangi diğer yayılan koduyla dinamik yöntem yürütme dinamik yöntem kullandığı yöntemleri tarafından talep edilen tüm izinler gerektirir.  
  
 Anonim olarak barındırılan dinamik yöntemler barındıran sistem derlemesi kullanan <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> önce .NET Framework 4 .NET Framework'teki kullanılan saydamlık modeli olan saydamlık modeli.  
  
 Daha fazla bilgi için <xref:System.Reflection.Emit.DynamicMethod> sınıfı.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Oluşturma anonim olarak barındırılan dinamik yöntemler kısmen güvenilen koddan  
 Internet izinlerine sahip bir derleme anonim olarak barındırılan dinamik bir yöntem oluşturmak ve çalıştırmak koşulları göz önünde bulundurun:  
  
- Dinamik yöntem, yalnızca genel türleri ve üyelerini kullanır. Kendi izin kümesini içeriyorsa <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>ortakdeğil türlere kullanabilirsiniz ve herhangi bir derleme, verme kümesi üyeleri eşit ya da bir alt kümesini, yayan derlemenin izin kümesi olması.  
  
- Tüm türler ve üyeler dinamik yöntemi tarafından kullanılan gerekli olan izinler kısmen güvenilen bir derlemede izin kümesi dahil edilir.  
  
> [!NOTE]
>  Dinamik yöntemler, hata ayıklama sembolleri desteklemez.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>   
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Dinamik yöntemler varolan derlemeleri ile ilişkili  
 Dinamik bir yöntem bir tür veya var olan bir derlemede modülü ilişkilendirmek için herhangi birini kullanmak <xref:System.Reflection.Emit.DynamicMethod> oluşturucular ilişkili typ nebo modul belirtin. Dinamik bir yöntem var olan bir türü ile ilişkili olduğundan bu oluşturucuları çağırmak için gereken izinler farklılık veya modül dinamik yöntem ortak olmayan türler ve üyeler için erişmenizi sağlar:  
  
- Bir türü ile ilişkili olan dinamik bir yöntem türü, hatta özel üyeler, tüm üyeleri erişebilir ve ilişkili türü içeren tüm iç türlerine ve üyelerine derlemedeki.  
  
- Bir modül ile ilişkili olan dinamik bir yöntem tüm erişimi olan `internal` türler ve üyeler (`Friend` Visual Basic'te `assembly` ortak dil çalışma zamanı meta verilerinde) modülünde.  
  
 Ayrıca, görünürlüğü atlama yeteneği JIT Derleyici denetler belirten bir oluşturucu kullanabilirsiniz. Bunun yapılması, dinamik yöntem tüm türlerine ve üyelerine erişim düzeyi ne olursa olsun tüm derlemelerde erişmenizi sağlar.  
  
 Oluşturucu tarafından talep edilen izinler bağlıdır, dinamik yöntem vermek karar ne kadar erişimi:  
  
- Yönteminiz yalnızca genel türleri ve üyeleri kullanıyorsa ve kendi türü veya kendi modülünüzü ile ilişkilendirmek, hiçbir izinleri gereklidir.  
  
- Oluşturucu, JIT görünürlük denetimlerini atlanması gerektiğini belirtirseniz, talepleri <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağı.  
  
- Dinamik yöntem başka bir tür ile ilişkilendirirseniz, kendi derlemesi içindeki başka bir tür Oluşturucu talepleri bile <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağı ve <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> bayrağı.  
  
- Dinamik yöntem bir tür veya başka bir derlemede modülü ile ilişkilendirirseniz, Oluşturucu iki şey talepleri: <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağı ve başka bir modül içeren derleme izin kümesi. Diğer bir deyişle, tüm izinleri hedef modülü izin kümesi çağrı yığınınızı içermelidir yanı sıra <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.  
  
    > [!NOTE]
    >  Hedef talep kümesi sağlıyorsa geriye dönük uyumluluk için artı <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> başarısız olursa Oluşturucusu taleplerini <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> bayrağı.  
  
 Bu listedeki öğeler bakımından izin kümesi yayan derlemenin açıklanan olsa da, uygulama etki alanı sınırları dahil olmak üzere tam çağrı yığınını karşı taleplerini yapıldığını unutmayın.  
  
 Daha fazla bilgi için <xref:System.Reflection.Emit.DynamicMethod> sınıfı.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Dinamik yöntemler kısmen güvenilen koddan oluşturma  
  
> [!NOTE]
>  Dinamik yöntemler kısmen güvenilen kod oluşturmak için önerilen yöntem kullanmaktır [anonim olarak barındırılan dinamik yöntemler](#Anonymously_Hosted_Dynamic_Methods).  
  
 Internet izinlerine sahip bir derleme dinamik bir yöntem oluşturmak ve çalıştırmak koşulları göz önünde bulundurun:  
  
- Dinamik yöntem modül veya kendisini çıkaran derlemeninkinden türü ile ilişkili veya kendi izin kümesini içeren <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> ve izni olan bir modül bir derleme ile ilişkili eşit ya da bir alt kümesini, yayan derlemenin izin kümesi kümesidir.  
  
- Dinamik yöntem, yalnızca genel türleri ve üyelerini kullanır. Kendi izin kümesini içeriyorsa <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> ve izni olan bir modül bir derleme ile ilişkili kümesi eşit ya da bir alt kümesini, yayan derlemenin izin kümesi, türler ve üyeler işaretlenmiş kullanabilirsiniz `internal` (`Friend` Visual Basic'te `assembly`ortak dil çalışma zamanı meta verilerinde) ilişkilendirilmiş modülü içinde.  
  
- Kısmen güvenilen bir derlemede izin kümesi, dinamik yöntem tarafından kullanılan üyeleri ve türleri tarafından talep edilen izinler dahil edilir.  
  
- Dinamik yöntem, JIT görünürlük denetimlerini atlamasını değil.  
  
> [!NOTE]
>  Dinamik yöntemler, hata ayıklama sembolleri desteklemez.  
  
<a name="Version_Information"></a>   
## <a name="version-information"></a>Sürüm Bilgileri  
 .NET Framework 4 ile başlayarak, makine genelindeki güvenlik ilkesi elenir ve güvenlik saydamlık varsayılan zorlama mekanizması olur. Bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
 İle başlayarak [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> bayrağı olduğunda artık gerekli dinamik derlemeler ve dinamik yöntemleri yayma. .NET Framework'ün tüm önceki sürümlerinde bu bayrağı gereklidir.  
  
> [!NOTE]
>  <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> bayrak varsayılan olarak dahil `FullTrust` ve `LocalIntranet` adlandırılmış izin kümelerine, ancak içinde olmayan `Internet` izin kümesi. Yalnızca yürütür, bu nedenle, önceki .NET Framework sürümlerinde, bir kitaplık Internet izinlerle kullanılabilir bir <xref:System.Security.PermissionSet.Assert%2A> için <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Kodlama hataları güvenlik açıklarına neden olabileceğinden tür kitaplıkların dikkatli bir güvenlik incelemesinden geçmesi gerekir. [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] Çünkü kod oluşturma herhangi bir güvenlik talebi verme doğası gereği ayrıcalıklı bir işlem değil olmadan kısmi güvenlik senaryolarına yayılmasını sağlar. Diğer bir deyişle, oluşturulan kod, yayan derlemenin daha fazla izne sahiptir. Böylece, güvenliği saydam kod yayan ve ihtiyacını kaldırır kitaplıkları <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, güvenli bir kitaplık yazma görevini basitleştirir.  
  
 Ayrıca, [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] tanıtır <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> ortakdeğil türlere ve üye kısmen güvenilen dinamik yöntemleri erişmek için bayrak. .NET Framework'ün önceki sürümlerini gerektirir <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrak ortak olmayan türler ve üyeler erişen dinamik yöntemler için; bu kısmen güvenilen koda hiçbir zaman verilen bir izni.  
  
 Son olarak, [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] anonim olarak barındırılan yöntemleri tanıtır.  
  
### <a name="obtaining-information-on-types-and-members"></a>Türler ve üyeler hakkında bilgi edinme  
 İle başlayarak [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], ortak olmayan türler ve üyeler hakkında bilgi edinmek için hiçbir izinleri gereklidir. Yansıma yayma dinamik yöntemler için gereken bilgileri elde etmek için kullanılır. Örneğin, <xref:System.Reflection.MethodInfo> nesneleri, yöntem çağrılarını yaymak için kullanılır. .NET Framework'ün önceki sürümlerini gerektirir <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> bayrağı. Daha fazla bilgi için [yansımayla ilgili güvenlik konuları](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansımayla İlgili Güvenlik Konuları](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
- [Dinamik Yöntemleri ve Derlemeleri Yayma](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)
