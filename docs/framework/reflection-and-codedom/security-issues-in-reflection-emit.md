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
ms.openlocfilehash: f04b40edde0755315f3b4fd4284fc7c804a54313
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130037"
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
 Dinamik derlemeler <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> yönteminin aşırı yüklemeleri kullanılarak oluşturulur. Bu yöntemin en fazla aşırı yüklemesi, makine genelinde güvenlik ilkesinin eliminasyon nedeniyle .NET Framework 4 ' te kullanım dışıdır. (Bkz. [güvenlik değişiklikleri](../security/security-changes.md).) Kalan aşırı yüklemeler, güven düzeyinden bağımsız olarak herhangi bir kod tarafından yürütülebilir. Bu aşırı yüklemeler iki gruba ayrılır: oluşturulduğu sırada dinamik derlemeye uygulanacak özniteliklerin bir listesini ve bunları belirtenler. Oluşturma işlemi sırasında <xref:System.Security.SecurityRulesAttribute> özniteliğini uygulayarak derleme için saydamlık modelini belirtmezseniz, saydam model, yayma derlemesinden devralınır.  
  
> [!NOTE]
> Oluşturulduktan sonra dinamik derleme için uyguladığınız öznitelikler, <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> yöntemi kullanılarak, derleme diske kaydedilip belleğe yeniden yüklenene kadar etkili olmaz.  
  
 Dinamik bir derlemedeki kod, diğer derlemelerdeki görünür türlere ve üyelere erişebilir.  
  
> [!NOTE]
> Dinamik derlemeler, dinamik yöntemlerin ortak türlere ve üyelere erişmesine izin veren <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> ve <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayraklarını kullanmaz.  
  
 Geçici dinamik derlemeler bellekte oluşturulur ve hiçbir şekilde diske kaydedilmez, bu nedenle dosya erişim izinleri gerektirmez. Dinamik bir derlemeyi diske kaydetmek için uygun bayraklarla <xref:System.Security.Permissions.FileIOPermission> gerekir.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Kısmen güvenilen koddan dinamik derlemeler oluşturma  
 Internet izinleri olan bir derlemenin geçici bir dinamik derleme oluşturabileceği ve kodunu yürütebileceği koşulları göz önünde bulundurun:  
  
- Dinamik derleme yalnızca ortak türleri ve diğer derlemelerin üyelerini kullanır.  
  
- Bu türler ve Üyeler tarafından talep edilen izinler kısmen güvenilen derlemenin izin kümesine dahil edilir.  
  
- Derleme diske kaydedilmez.  
  
- Hata ayıklama sembolleri oluşturulmaz. (`Internet` ve `LocalIntranet` izin kümeleri gerekli izinleri içermez.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>   
## <a name="anonymously-hosted-dynamic-methods"></a>Anonim olarak barındırılan dinamik yöntemler  
 Anonim olarak barındırılan dinamik yöntemler, <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> ve <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>bir ilişkili tür veya modül belirtmeyen iki <xref:System.Reflection.Emit.DynamicMethod> Oluşturucu kullanılarak oluşturulur. Bu oluşturucular, dinamik metotları sistem tarafından sağlanmış, tam güvenilir, güvenlik açısından saydam bir derlemeye yerleştirir. Bu oluşturucuları kullanmak veya dinamik yöntemler için kod göstermek için izin gerekmez.  
  
 Bunun yerine, anonim olarak barındırılan bir dinamik yöntem oluşturulduğunda, çağrı yığını yakalanır. Yöntem oluşturulduğunda, yakalanan çağrı yığınına karşı güvenlik istekleri yapılır.  
  
> [!NOTE]
> Kavramsal olarak, yöntemin oluşturulması sırasında talepler yapılır. Diğer bir deyişle, her MSIL yönergesi yayıldığından talepler yapılabilir. Geçerli uygulamada, <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> yöntemi çağrıldığında veya yöntem <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>çağırılmadan çağrıldığında, tek seferlik (JıT) derleyicisi çağrıldığında tüm talepler yapılır.  
  
 Uygulama etki alanı izin veriyorsa, anonim olarak barındırılan dinamik yöntemler JıT görünürlük denetimlerini atlayabilir ve aşağıdaki kısıtlamaya tabidir: anonim olarak barındırılan dinamik bir yöntem tarafından erişilen ortak türler ve Üyeler, izin kümeleri olan derlemelerde olmalıdır , yayma çağrısı yığınının izin kümesine eşittir veya alt kümelerine eşittir. Uygulama etki alanı <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission> veriyorsa, JıT görünürlük denetimlerini atlayabilme özelliği bu kısıtlı olur.  
  
- Yönteminiz yalnızca ortak türleri ve üyeleri kullanıyorsa, oluşturma sırasında izin gerekmez.  
  
- JıT görünürlük denetimlerinin atlanacağını belirtirseniz, yöntem oluşturulduğunda yapılan talep, <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission> ve erişilmekte olan ortak üyeyi içeren derlemenin izin kümesini içerir.  
  
 Ortak üyenin izin kümesi dikkate alındığından, kısmen güvenilen kod <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, güvenilen derlemelerin ortak üyelerini yürüterek ayrıcalık yükselmez.  
  
 Diğer herhangi bir yayınlanan kodda olduğu gibi, dinamik yöntemin yürütülmesi, dinamik yöntemin kullandığı yöntemler tarafından talep edilen izinlerin her birini gerektirir.  
  
 Anonim olarak barındırılan dinamik yöntemler barındıran sistem derlemesi, .NET Framework 4 ' ten önceki .NET Framework kullanılan saydamlık modeli olan <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> saydamlık modelini kullanır.  
  
 Daha fazla bilgi için <xref:System.Reflection.Emit.DynamicMethod> sınıfına bakın.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Kısmen güvenilen koddan anonim olarak barındırılan dinamik yöntemler oluşturma  
 Internet izinleri olan bir derlemenin anonim olarak barındırılan dinamik bir yöntem oluşturabileceği ve bunu yürütebileceği koşulları göz önünde bulundurun:  
  
- Dinamik yöntem yalnızca ortak türleri ve üyeleri kullanır. Verme kümesi <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>içeriyorsa, izin kümesi eşit olan veya bir alt kümesi olan herhangi bir derlemenin ortak türlerini ve üyelerini, yayma derlemesinin izin kümesini kullanabilir.  
  
- Dinamik yöntem tarafından kullanılan tüm türler ve Üyeler için gereken izinler, kısmen güvenilen derlemenin izin kümesine dahil edilir.  
  
> [!NOTE]
> Dinamik yöntemler hata ayıklama sembollerini desteklemez.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>   
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Mevcut Derlemelerle Ilişkili dinamik yöntemler  
 Dinamik bir yöntemi varolan bir derlemedeki bir tür veya modülle ilişkilendirmek için, ilişkili tür veya modülü belirten <xref:System.Reflection.Emit.DynamicMethod> oluşturucularından birini kullanın. Bu oluşturucuları çağırmak için gereken izinler, dinamik bir yöntemi varolan bir tür veya modülle ilişkilendirirken, dinamik yöntemin ortak olmayan türlere ve üyelere erişmesini sağladığından değişiklik gösterir.  
  
- Bir türle ilişkili dinamik bir yöntem, bu türdeki tüm üyelere, hatta özel üyelere ve ilişkili türü içeren derlemedeki tüm iç türlere ve üyelere erişim sağlar.  
  
- Modülle ilişkili dinamik bir yöntem, modüldeki tüm `internal` türlerine ve üyelere (Visual Basic`Friend`, ortak dil çalışma zamanı meta verilerinde `assembly`) erişimi vardır.  
  
 Ayrıca, JıT derleyicisinin görünürlük denetimlerini atlama yeteneğini belirten bir Oluşturucu kullanabilirsiniz. Bunun yapılması, erişim düzeyinden bağımsız olarak, dinamik yönteminizin tüm derlemelerdeki tüm türlere ve üyelere erişmesini sağlar.  
  
 Oluşturucu tarafından talep edilen izinler, dinamik yönteminizin ne kadar erişime izin verdiğinize bağlıdır:  
  
- Yönteminiz yalnızca ortak türleri ve üyeleri kullanıyorsa ve bunu kendi türü veya kendi modülle ilişkilendirirseniz, izin gerekmez.  
  
- JıT görünürlük denetimlerinin atlanacağını belirtirseniz, Oluşturucu <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission> talep eder.  
  
- Dinamik yöntemi başka bir türle (hatta kendi derlemenizin başka bir tür) ilişkilendirirseniz, Oluşturucu <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission> ve <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.SecurityPermission>.  
  
- Dinamik yöntemi başka bir derlemede bir tür veya modülle ilişkilendirirseniz, Oluşturucu iki şey ister: <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission> ve diğer modülün bulunduğu derlemenin izin kümesi. Diğer bir deyişle, çağrı yığınınızın, hedef modülün izin kümesine ve <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>tüm izinleri içermesi gerekir.  
  
    > [!NOTE]
    > Geriye dönük uyumluluk için, hedef izin kümesi ve <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> için talep başarısız olursa, Oluşturucu <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.SecurityPermission>.  
  
 Bu listedeki öğeler, yayma derlemesinin izin kümesi bakımından açıklansa da, taleplerin, uygulama etki alanı sınırı dahil olmak üzere tam çağrı yığınına göre yapıldığını unutmayın.  
  
 Daha fazla bilgi için <xref:System.Reflection.Emit.DynamicMethod> sınıfına bakın.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Kısmen güvenilen koddan dinamik yöntemler oluşturma  
  
> [!NOTE]
> Kısmen güvenilen koddan dinamik yöntemler oluşturmanın önerilen yolu, [anonim olarak barındırılan dinamik yöntemler](#Anonymously_Hosted_Dynamic_Methods)kullanmaktır.  
  
 Internet izinlerine sahip bir derlemenin dinamik bir yöntem oluşturabileceği ve bunu yürütebileceği koşulları göz önünde bulundurun:  
  
- Dinamik yöntem, onu gösteren modülle veya tür ile ilişkili ya da izin kümesi <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> içerir ve veren derlemesinin izin kümesi olan bir derleme içindeki bir modülle ilişkilendirilir.  
  
- Dinamik yöntem yalnızca ortak türleri ve üyeleri kullanır. Verme kümesi <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> içeriyorsa ve bu bir derlemede, verme kümesi eşittir veya bir alt kümesi olan derleme içindeki bir modülle ilişkiliyse, `internal` işaretlenmiş türleri ve üyeleri kullanabilir (`Friend` Visual Basic , ilişkili modüldeki ortak dil çalışma zamanı meta verilerinde `assembly`).  
  
- Dinamik yöntem tarafından kullanılan tüm türler ve Üyeler tarafından talep edilen izinler, kısmen güvenilen derlemenin izin kümesine dahil edilir.  
  
- Dinamik yöntem JıT görünürlük denetimlerini atlamaz.  
  
> [!NOTE]
> Dinamik yöntemler hata ayıklama sembollerini desteklemez.  
  
<a name="Version_Information"></a>   
## <a name="version-information"></a>Sürüm Bilgileri  
 .NET Framework 4 ' te başlayarak, makine genelinde güvenlik ilkesi ortadan kalkar ve güvenlik saydamlığı varsayılan zorlama mekanizması haline gelir. Bkz. [güvenlik değişiklikleri](../security/security-changes.md).  
  
 .NET Framework 2,0 hizmet paketi 1 ' den başlayarak, dinamik derlemeler ve dinamik yöntemler yayırken <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission> artık gerekli değildir. Bu bayrak, .NET Framework önceki tüm sürümlerinde gereklidir.  
  
> [!NOTE]
> <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission>, `FullTrust` varsayılan olarak dahil edilir ve `Internet` izin kümesi içinde değil, adlandırılmış izin kümeleri `LocalIntranet`. Bu nedenle, .NET Framework önceki sürümlerinde, bir kitaplık yalnızca <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>için bir <xref:System.Security.PermissionSet.Assert%2A> yürüttüğünde Internet izinleriyle kullanılabilir. Bu tür Kitaplıklar, kodlama hataları güvenlik delikleri ile sonuçlanabileceğinden dikkatli bir güvenlik incelemesi gerektirir. .NET Framework 2,0 SP1, kod oluşturma doğal olarak ayrıcalıklı bir işlem olmadığından kodun herhangi bir güvenlik talebi vermeden kısmi güven senaryolarında oluşturulmasına olanak sağlar. Diğer bir deyişle, oluşturulan kodun onu yayan derlemeden daha fazla izni yoktur. Bu, kod veren kitaplıkların güvenlik açısından saydam olmasını sağlar ve güvenli bir kitaplık yazma görevini kolaylaştıran <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>onay gereksinimini ortadan kaldırır.  
  
 Ayrıca, .NET Framework 2,0 SP1, kısmen güvenilen dinamik metotlardan ortak türlere ve üyelere erişim için <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağını tanıtır. .NET Framework önceki sürümleri, özel türler ve üyelere erişen dinamik yöntemler için <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağını gerektirir; Bu, kısmen güvenilen koda asla verilmemesi gereken bir izindir.  
  
 Son olarak, .NET Framework 2,0 SP1 anonim olarak barındırılan yöntemler sunar.  
  
### <a name="obtaining-information-on-types-and-members"></a>Türler ve Üyeler hakkında bilgi edinme  
 .NET Framework 2,0 ' den başlayarak, özel türler ve Üyeler hakkında bilgi edinmek için izin gerekmez. Yansıma, dinamik yöntemleri yayma için gereken bilgileri almak için kullanılır. Örneğin, <xref:System.Reflection.MethodInfo> nesneler Yöntem çağrılarını göstermek için kullanılır. .NET Framework önceki sürümlerinde <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission> gerekir. Daha fazla bilgi için bkz. [yansıma Için güvenlik konuları](security-considerations-for-reflection.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansımayla İlgili Güvenlik Konuları](security-considerations-for-reflection.md)
- [Dinamik Yöntemleri ve Derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)
