---
title: Yansıma Yaymadaki Güvenlik Sorunları
description: Yansıma Yaymadaki, dinamik derlemeler veya var olan Derlemelerle veya anonim olarak barındırılan dinamik yöntemler aracılığıyla gerçekleştirilen güvenlik sorunlarını öğrenin.
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
ms.openlocfilehash: d0ca26a1d0964c935137b0a30a5d7c78f93c597b
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865248"
---
# <a name="security-issues-in-reflection-emit"></a>Yansıma Yaymadaki Güvenlik Sorunları
.NET Framework, her biri kendi güvenlik sorunlarıyla birlikte Microsoft ara dili 'ni (MSIL) yaymanın üç yolunu sunar:  
  
- [Dinamik derlemeler](#Dynamic_Assemblies)  
  
- [Anonim olarak barındırılan dinamik yöntemler](#Anonymously_Hosted_Dynamic_Methods)  
  
- [Mevcut Derlemelerle ilişkili dinamik yöntemler](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Dinamik kod oluşturma yönteminden bağımsız olarak, oluşturulan kodun yürütülmesi oluşturulan kodun kullandığı türler ve yöntemler için gereken tüm izinleri gerektirir.  
  
> [!NOTE]
> Kod ve yayma kodu üzerinde yansıtma için gereken izinler, .NET Framework sonraki sürümleriyle değiştirilmiştir. Bu konunun devamındaki [sürüm bilgilerine](#Version_Information)bakın.  
  
<a name="Dynamic_Assemblies"></a>
## <a name="dynamic-assemblies"></a>Dinamik derlemeler  
 Dinamik derlemeler, yönteminin aşırı yüklemeleri kullanılarak oluşturulur <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> . Bu yöntemin en fazla aşırı yüklemesi, makine genelinde güvenlik ilkesinin eliminasyon nedeniyle .NET Framework 4 ' te kullanım dışıdır. (Bkz. [güvenlik değişiklikleri](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).) Kalan aşırı yüklemeler, güven düzeyinden bağımsız olarak herhangi bir kod tarafından yürütülebilir. Bu aşırı yüklemeler iki gruba ayrılır: oluşturulduğu sırada dinamik derlemeye uygulanacak özniteliklerin bir listesini ve bunları belirtenler. Derleme için saydamlık modelini belirtmezseniz, <xref:System.Security.SecurityRulesAttribute> Bu özniteliği oluşturduğunuzda uyguladığınızda, saydam model, yayma derlemesinden devralınır.  
  
> [!NOTE]
> Oluşturulduktan sonra dinamik derleme için uyguladığınız öznitelikler yöntemi kullanılarak, <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> derleme diske kaydedilinceye ve yeniden belleğe yükleninceye kadar etkili olmaz.  
  
 Dinamik bir derlemedeki kod, diğer derlemelerdeki görünür türlere ve üyelere erişebilir.  
  
> [!NOTE]
> Dinamik derlemeler, <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> dinamik yöntemlerin ortak türlere ve üyelere erişmesine izin veren ve bayraklarını kullanmaz.  
  
 Geçici dinamik derlemeler bellekte oluşturulur ve hiçbir şekilde diske kaydedilmez, bu nedenle dosya erişim izinleri gerektirmez. Dinamik bir derlemeyi diske kaydetmek için <xref:System.Security.Permissions.FileIOPermission> uygun bayraklar gerekir.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Kısmen güvenilen koddan dinamik derlemeler oluşturma  
 Internet izinleri olan bir derlemenin geçici bir dinamik derleme oluşturabileceği ve kodunu yürütebileceği koşulları göz önünde bulundurun:  
  
- Dinamik derleme yalnızca ortak türleri ve diğer derlemelerin üyelerini kullanır.  
  
- Bu türler ve Üyeler tarafından talep edilen izinler kısmen güvenilen derlemenin izin kümesine dahil edilir.  
  
- Derleme diske kaydedilmez.  
  
- Hata ayıklama sembolleri oluşturulmaz. ( `Internet` ve `LocalIntranet` izin kümeleri gerekli izinleri içermez.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>
## <a name="anonymously-hosted-dynamic-methods"></a>Anonim olarak barındırılan dinamik yöntemler  
 Anonim olarak barındırılan dinamik yöntemler <xref:System.Reflection.Emit.DynamicMethod> , ilişkili tür veya modül belirtmeyen iki Oluşturucu kullanılarak oluşturulur <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> ve <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> . Bu oluşturucular, dinamik metotları sistem tarafından sağlanmış, tam güvenilir, güvenlik açısından saydam bir derlemeye yerleştirir. Bu oluşturucuları kullanmak veya dinamik yöntemler için kod göstermek için izin gerekmez.  
  
 Bunun yerine, anonim olarak barındırılan bir dinamik yöntem oluşturulduğunda, çağrı yığını yakalanır. Yöntem oluşturulduğunda, yakalanan çağrı yığınına karşı güvenlik istekleri yapılır.  
  
> [!NOTE]
> Kavramsal olarak, yöntemin oluşturulması sırasında talepler yapılır. Diğer bir deyişle, her MSIL yönergesi yayıldığından talepler yapılabilir. Geçerli uygulamada, yöntem <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> çağrıldığında veya yöntem çağrılmadan çağrılırsa, tek seferlik (JIT) derleyicisi çağrıldığında tüm talepler yapılır <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> .  
  
 Uygulama etki alanı izin veriyorsa, anonim olarak barındırılan dinamik yöntemler JıT görünürlük denetimlerini atlayabilir ve aşağıdaki kısıtlamaya tabidir: anonim olarak barındırılan dinamik bir yöntem tarafından erişilen ortak türler ve Üyeler, verme çağrısı yığınının verme kümesine eşit veya alt kümelerine sahip olan derlemelerde olmalıdır. Uygulama etki alanı bayrağa veriyorsa, JıT görünürlük denetimlerini atlayabilme özelliği bu kısıtlı olur <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> .  
  
- Yönteminiz yalnızca ortak türleri ve üyeleri kullanıyorsa, oluşturma sırasında izin gerekmez.  
  
- JıT görünürlük denetimlerinin atlanacağını belirtirseniz, yöntem oluşturulduğunda yapılan istek, <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> erişildiği ortak üyeyi içeren derlemenin ve izin kümesi ile birlikte içerir.  
  
 Ortak üyenin izin kümesi dikkate alındığından, kısmen güvenilen kod, <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> Güvenilen derlemelerin ortak üyelerini yürüterek ayrıcalık yükselmez.  
  
 Diğer herhangi bir yayınlanan kodda olduğu gibi, dinamik yöntemin yürütülmesi, dinamik yöntemin kullandığı yöntemler tarafından talep edilen izinlerin her birini gerektirir.  
  
 Anonim olarak barındırılan dinamik yöntemler barındıran sistem derlemesi, <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> .NET Framework 4 ' ten önce .NET Framework kullanılan saydamlık modeli olan saydamlık modelini kullanır.  
  
 Daha fazla bilgi için, <xref:System.Reflection.Emit.DynamicMethod> sınıfına bakın.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Kısmen güvenilen koddan anonim olarak barındırılan dinamik yöntemler oluşturma  
 Internet izinleri olan bir derlemenin anonim olarak barındırılan dinamik bir yöntem oluşturabileceği ve bunu yürütebileceği koşulları göz önünde bulundurun:  
  
- Dinamik yöntem yalnızca ortak türleri ve üyeleri kullanır. Verme kümesi şunları içeriyorsa <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> , verme derlemesinin izin kümesi veya bir alt kümesi olan herhangi bir derlemenin ortak türlerini ve üyelerini, yayma derlemesinin verme kümesini kullanabilir.  
  
- Dinamik yöntem tarafından kullanılan tüm türler ve Üyeler için gereken izinler, kısmen güvenilen derlemenin izin kümesine dahil edilir.  
  
> [!NOTE]
> Dinamik yöntemler hata ayıklama sembollerini desteklemez.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Mevcut Derlemelerle Ilişkili dinamik yöntemler  
 Dinamik bir yöntemi varolan bir derlemedeki bir tür veya modülle ilişkilendirmek için, <xref:System.Reflection.Emit.DynamicMethod> ilişkili tür veya modülü belirten oluşturuculardan birini kullanın. Bu oluşturucuları çağırmak için gereken izinler, dinamik bir yöntemi varolan bir tür veya modülle ilişkilendirirken, dinamik yöntemin ortak olmayan türlere ve üyelere erişmesini sağladığından değişiklik gösterir.  
  
- Bir türle ilişkili dinamik bir yöntem, bu türdeki tüm üyelere, hatta özel üyelere ve ilişkili türü içeren derlemedeki tüm iç türlere ve üyelere erişim sağlar.  
  
- Modülle ilişkili dinamik bir yöntem, `internal` modüldeki tüm türlere ve üyelere ( `Friend` `assembly` ortak dil çalışma zamanı meta verilerinde Visual Basic) erişebilir.  
  
 Ayrıca, JıT derleyicisinin görünürlük denetimlerini atlama yeteneğini belirten bir Oluşturucu kullanabilirsiniz. Bunun yapılması, erişim düzeyinden bağımsız olarak, dinamik yönteminizin tüm derlemelerdeki tüm türlere ve üyelere erişmesini sağlar.  
  
 Oluşturucu tarafından talep edilen izinler, dinamik yönteminizin ne kadar erişime izin verdiğinize bağlıdır:  
  
- Yönteminiz yalnızca ortak türleri ve üyeleri kullanıyorsa ve bunu kendi türü veya kendi modülle ilişkilendirirseniz, izin gerekmez.  
  
- JıT görünürlük denetimlerinin atlanacağını belirtirseniz, Oluşturucu bayrağıyla talep eder <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> .  
  
- Dinamik yöntemi başka bir türle, hatta kendi derlemenizin başka bir tür ile ilişkilendirirseniz, Oluşturucu ile ve bayrağıyla birlikte talep edersiniz <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> <xref:System.Security.Permissions.SecurityPermission> <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> .  
  
- Dinamik yöntemi başka bir derlemede bir tür veya modülle ilişkilendirirseniz, Oluşturucu iki şey ister: <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağıyla ve diğer modülü içeren derlemenin izin kümesi. Diğer bir deyişle, çağrı yığınınızın, hedef modülün izin kümesine ve ek olarak tüm izinleri içermesi gerekir <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> .  
  
    > [!NOTE]
    > Geriye dönük uyumluluk için, hedef verme kümesine yönelik talep ve <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> başarısız olursa, Oluşturucu bayrağıyla talep edilir <xref:System.Security.Permissions.SecurityPermission> <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> .  
  
 Bu listedeki öğeler, yayma derlemesinin izin kümesi bakımından açıklansa da, taleplerin, uygulama etki alanı sınırı dahil olmak üzere tam çağrı yığınına göre yapıldığını unutmayın.  
  
 Daha fazla bilgi için, <xref:System.Reflection.Emit.DynamicMethod> sınıfına bakın.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Kısmen güvenilen koddan dinamik yöntemler oluşturma  
  
> [!NOTE]
> Kısmen güvenilen koddan dinamik yöntemler oluşturmanın önerilen yolu, [anonim olarak barındırılan dinamik yöntemler](#Anonymously_Hosted_Dynamic_Methods)kullanmaktır.  
  
 Internet izinlerine sahip bir derlemenin dinamik bir yöntem oluşturabileceği ve bunu yürütebileceği koşulları göz önünde bulundurun:  
  
- Dinamik yöntem, kendisini gösteren modülle ya da türle ilişkili ya da izin kümesi içerir ve veren derlemesinin izin kümesi, <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> ya da bir alt kümesi olan derleme içindeki bir modülle ilişkilendirilir.  
  
- Dinamik yöntem yalnızca ortak türleri ve üyeleri kullanır. Verme kümesi içeriyorsa <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> ve bu bir derlemede, verme kümesi eşittir veya bir alt kümesi olan derleme içindeki bir modülle ilişkiliyse, `internal` `Friend` `assembly` ilişkili modüldeki (ortak dil çalışma zamanı meta verilerinde Visual Basic) işaretlenmiş türleri ve üyeleri kullanabilir.  
  
- Dinamik yöntem tarafından kullanılan tüm türler ve Üyeler tarafından talep edilen izinler, kısmen güvenilen derlemenin izin kümesine dahil edilir.  
  
- Dinamik yöntem JıT görünürlük denetimlerini atlamaz.  
  
> [!NOTE]
> Dinamik yöntemler hata ayıklama sembollerini desteklemez.  
  
<a name="Version_Information"></a>
## <a name="version-information"></a>Sürüm Bilgileri  
 .NET Framework 4 ' te başlayarak, makine genelinde güvenlik ilkesi ortadan kalkar ve güvenlik saydamlığı varsayılan zorlama mekanizması haline gelir. Bkz. [güvenlik değişiklikleri](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 .NET Framework 2,0 Service Pack 1 ' den başlayarak, <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> Dinamik derlemeler ve dinamik yöntemler yayırken bayrağı artık gerekli değildir. Bu bayrak, .NET Framework önceki tüm sürümlerinde gereklidir.  
  
> [!NOTE]
> <xref:System.Security.Permissions.ReflectionPermission>bayrağı ile <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> , `FullTrust` ve adlandırılmış izin kümelerinde varsayılan olarak dahil edilir `LocalIntranet` , ancak `Internet` izin kümesinde yoktur. Bu nedenle, .NET Framework önceki sürümlerinde, bir kitaplık yalnızca bir için yürütüldüğünde Internet izinleriyle birlikte kullanılabilir <xref:System.Security.PermissionSet.Assert%2A> <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit> . Bu tür Kitaplıklar, kodlama hataları güvenlik delikleri ile sonuçlanabileceğinden dikkatli bir güvenlik incelemesi gerektirir. .NET Framework 2,0 SP1, kod oluşturma doğal olarak ayrıcalıklı bir işlem olmadığından kodun herhangi bir güvenlik talebi vermeden kısmi güven senaryolarında oluşturulmasına olanak sağlar. Diğer bir deyişle, oluşturulan kodun onu yayan derlemeden daha fazla izni yoktur. Bu, kod veren kitaplıkların güvenlik açısından saydam olmasını sağlar ve <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit> güvenli bir kitaplık yazma görevini kolaylaştıran onay gereksinimini ortadan kaldırır.  
  
 Ayrıca, .NET Framework 2,0 SP1, <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> kısmen güvenilen dinamik metotlardan ortak türlere ve üyelere erişim bayrağını tanıtır. .NET Framework önceki sürümleri, <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> ortak olmayan türlere ve üyelere erişen dinamik yöntemler için bayrak gerektirir; Bu, kısmen güvenilen kod için asla verilmemesi gereken bir izindir.  
  
 Son olarak, .NET Framework 2,0 SP1 anonim olarak barındırılan yöntemler sunar.  
  
### <a name="obtaining-information-on-types-and-members"></a>Türler ve Üyeler hakkında bilgi edinme  
 .NET Framework 2,0 ' den başlayarak, özel türler ve Üyeler hakkında bilgi edinmek için izin gerekmez. Yansıma, dinamik yöntemleri yayma için gereken bilgileri almak için kullanılır. Örneğin, <xref:System.Reflection.MethodInfo> nesneler Yöntem çağrılarını yayma için kullanılır. .NET Framework önceki sürümleri <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> bayrağıyla gerektirir. Daha fazla bilgi için bkz. [yansıma Için güvenlik konuları](security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansımayla İlgili Güvenlik Konuları](security-considerations-for-reflection.md)
- [Dinamik Yöntemleri ve Derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)
