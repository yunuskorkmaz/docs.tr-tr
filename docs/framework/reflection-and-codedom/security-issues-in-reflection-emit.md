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
ms.openlocfilehash: 11eb4c9bc4ba1b1fe9051a04d12f893e693fb175
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180469"
---
# <a name="security-issues-in-reflection-emit"></a>Yansıma Yaymadaki Güvenlik Sorunları
.NET Framework, her biri kendi güvenlik sorunları olan Microsoft ara dilini (MSIL) yayan üç yol sağlar:  
  
- [Dinamik montajlar](#Dynamic_Assemblies)  
  
- [Anonim olarak barındırılan dinamik yöntemler](#Anonymously_Hosted_Dynamic_Methods)  
  
- [Varolan derlemelerle ilişkili dinamik yöntemler](#Dynamic_Methods_Associated_with_Existing_Assemblies)  
  
 Dinamik kodu oluşturma biçiminiz ne olursa olsun, oluşturulan kodu niçin yürüttüğün, oluşturulan kodun kullandığı tür ve yöntemlerin gerektirdiği tüm izinleri gerektirir.  
  
> [!NOTE]
> Kod ayansıtmak ve kod yayan için gereken izinler ,.NET Framework'ün sonraki sürümleriyle değiştirildi. Bu konunun ilerleyen saatlerinde [Sürüm Bilgileri'ne](#Version_Information)bakın.  
  
<a name="Dynamic_Assemblies"></a>
## <a name="dynamic-assemblies"></a>Dinamik Montajlar  
 Dinamik derlemeler <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> yöntemin aşırı yükleri kullanılarak oluşturulur. Bu yöntemin çoğu,makine genelinde güvenlik ilkesinin ortadan kaldırılması nedeniyle .NET Framework 4'te amortismana ayrılır. (Bkz. [Güvenlik Değişiklikleri](../security/security-changes.md).) Kalan aşırı yüklemeler, güven düzeyine bakılmaksızın herhangi bir kod tarafından yürütülebilir. Bu aşırı yüklemeler iki gruba ayrılır: oluşturulduğunda dinamik derlemeye uygulanacak özniteliklerin listesini belirtenler ve olmayanlar. Derleme için saydamlık modelini belirtmezseniz, <xref:System.Security.SecurityRulesAttribute> oluşturduğunuzda özniteliği uygulayarak, saydamlık modeli yayan derlemeden devralır.  
  
> [!NOTE]
> Oluşturulduktan sonra dinamik derlemeye uyguladığınız öznitelikler, <xref:System.Reflection.Emit.AssemblyBuilder.SetCustomAttribute%2A> yöntemi kullanarak, derleme diske kaydedilip yeniden belleğe yüklenene kadar etkili olmaz.  
  
 Dinamik bir derlemedeki kod, diğer derlemelerde görünür türlere ve üyelere erişebilir.  
  
> [!NOTE]
> Dinamik derlemeler, dinamik <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> yöntemlerin genel olmayan türlere ve üyelere erişmesine izin veren ve bayraklar kullanmaz.  
  
 Geçici dinamik derlemeler bellekte oluşturulur ve hiçbir zaman diske kaydedilmez, bu nedenle dosya erişim izinleri gerektirmez. Dinamik bir derlemeyi <xref:System.Security.Permissions.FileIOPermission> diske kaydetmek için uygun bayraklarla birlikte gerekir.  
  
### <a name="generating-dynamic-assemblies-from-partially-trusted-code"></a>Kısmen Güvenilen Koddan Dinamik Derlemeler Oluşturma  
 Internet izinleri olan bir derlemenin geçici dinamik bir derleme oluşturup kodunu yürütebileceği koşulları göz önünde bulundurun:  
  
- Dinamik derleme yalnızca genel türleri ve diğer derlemelerin üyelerini kullanır.  
  
- Bu tür ve üyeler tarafından talep edilen izinler, kısmen güvenilen derlemenin hibe kümesine dahil edilir.  
  
- Derleme diske kaydedilmez.  
  
- Hata ayıklama sembolleri oluşturulmaz. (`Internet` `LocalIntranet` ve izin setleri gerekli izinleri içermez.)  
  
<a name="Anonymously_Hosted_Dynamic_Methods"></a>
## <a name="anonymously-hosted-dynamic-methods"></a>Anonim Barındırılan Dinamik Yöntemler  
 Anonim olarak barındırılan dinamik yöntemler, <xref:System.Reflection.Emit.DynamicMethod> <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%29> ilişkili bir tür veya modül belirtmeyen <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29>iki oluşturucu kullanılarak oluşturulur ve. Bu oluşturucular dinamik yöntemleri sistem tarafından sağlanan, tamamen güvenilir, güvenlik saydam bir derlemeye yerletirler. Bu oluşturucuları kullanmak veya dinamik yöntemler için kod oluşturmak için izin gerekmez.  
  
 Bunun yerine, anonim olarak barındırılan dinamik bir yöntem oluşturulduğunda, çağrı yığını yakalanır. Yöntem oluşturulduğunda, yakalanan çağrı yığınına karşı güvenlik talepleri yapılır.  
  
> [!NOTE]
> Kavramsal olarak, talepler yöntemin inşası sırasında yapılır. Diğer bir süre, her MSIL yürüyüşü yayınlanırken talepler yapılabilir. Geçerli uygulamada, <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A?displayProperty=nameWithType> tüm talepler yöntem çağrıldığında veya tam zamanında (JIT) derleyici çağrıldığında, yöntem çağrılmadan <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>çağrıldığında yapılır.  
  
 Uygulama etki alanı buna izin verirse, anonim olarak barındırılan dinamik yöntemler JIT görünürlük denetimlerini atlayabilir, aşağıdaki kısıtlamaya tabidir: Anonim olarak barındırılan dinamik bir yöntemle erişilen genel olmayan türler ve üyeler, hibe kümeleri olan derlemelerde olmalıdır yayan çağrı yığınının hibe kümesine eşit veya alt kümeleri vardır. Uygulama etki alanı <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrakla hibe veriyorsa, JIT görünürlük denetimlerini atlamak için bu sınırlı yeteneği etkinleştirilir.  
  
- Yönteminiz yalnızca genel türleri ve üyeleri kullanıyorsa, inşaat sırasında izin gerekmez.  
  
- JIT görünürlük denetimlerinin atlanması gerektiğini belirtirseniz, yöntem oluşturulduğunda yapılan <xref:System.Security.Permissions.ReflectionPermission> talep, <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> erişilen genel olmayan üyeyi içeren derlemenin bayrak ve hibe kümesini içerir.  
  
 Kamu üyesi olmayan üyenin hibe seti dikkate alındığından, kısmen güvenilen <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> kod, güvenilen meclislerin kamuya açık olmayan üyelerini çalıştırarak ayrıcalıklarını yükseltemez.  
  
 Diğer yayılan kodlarda olduğu gibi, dinamik yöntemin yürütülmesi, dinamik yöntemin kullandığı yöntemlertarafından hangi izinlerin talep edildiğini gerektirir.  
  
 Anonim olarak barındırılan dinamik yöntemleri barındıran sistem derlemesi, .NET Framework 4'ten önce .NET Framework'de kullanılan saydamlık modeli olan <xref:System.Security.SecurityRuleSet.Level1?displayProperty=nameWithType> saydamlık modelini kullanır.  
  
 Daha fazla bilgi <xref:System.Reflection.Emit.DynamicMethod> için sınıfa bakın.  
  
### <a name="generating-anonymously-hosted-dynamic-methods-from-partially-trusted-code"></a>Kısmen Güvenilen Koddan Anonim Olarak Barındırılan Dinamik Yöntemler Oluşturma  
 Internet izinleri olan bir derlemenin anonim olarak barındırılan dinamik bir yöntem oluşturup çalıştırabileceği koşulları göz önünde bulundurun:  
  
- Dinamik yöntem yalnızca ortak türleri ve üyeleri kullanır. Hibe kümesi, <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>kamu dışı türleri ve hibe kümesi yayan derlemenin hibe kümesine eşit olan herhangi bir derlemenin üyelerini kullanabilir.  
  
- Dinamik yöntem tarafından kullanılan tüm türler ve üyeler tarafından gerekli olan izinler, kısmen güvenilen derlemenin hibe kümesine dahil edilir.  
  
> [!NOTE]
> Dinamik yöntemler hata ayıklama sembollerini desteklemez.  
  
<a name="Dynamic_Methods_Associated_with_Existing_Assemblies"></a>
## <a name="dynamic-methods-associated-with-existing-assemblies"></a>Varolan Derlemelerle İlişkili Dinamik Yöntemler  
 Dinamik bir yöntemi varolan bir derlemedeki bir tür veya <xref:System.Reflection.Emit.DynamicMethod> modülle ilişkilendirmek için, ilişkili türü veya modülü belirten yapıcılardan herhangi birini kullanın. Dinamik bir yöntemi varolan bir tür veya modülle ilişkilendirmek, dinamik yöntemin genel olmayan türlere ve üyelere erişmesini sağladığından, bu oluşturucuları çağırmak için gereken izinler farklılık gösterir:  
  
- Bir türle ilişkili dinamik bir yöntem, bu türdeki tüm üyelere, hatta özel üyelere ve ilişkili türü içeren derlemedeki tüm dahili türlere ve üyelere erişebilir.  
  
- Bir modülle ilişkili dinamik bir yöntem, `internal` modüldeki tüm`Friend` tür ve `assembly` üyelere (Visual Basic'te, ortak dilde çalışma zamanı meta verilerinde) erişebilir.  
  
 Ayrıca, JIT derleyicisinin görünürlük denetimlerini atlama yeteneğini belirten bir oluşturucu kullanabilirsiniz. Bunu yapmak, dinamik yönteminizin erişim düzeyine bakılmaksızın tüm derlemelerde tüm türve üyelere erişmenizi sağlar.  
  
 Oluşturucu tarafından talep edilen izinler, dinamik yönteminizi vermeye ne kadar erişim vermeye karar verdiğinize bağlıdır:  
  
- Yönteminiz yalnızca genel türleri ve üyeleri kullanıyorsa ve bunu kendi türünüzle veya kendi modülünüzle ilişkilendiriyorsanız, izin gerekmez.  
  
- JIT görünürlük denetimlerinin atlanınması gerektiğini belirtirseniz, <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> oluşturucu bayrakla birlikte talep eder. <xref:System.Security.Permissions.ReflectionPermission>  
  
- Dinamik yöntemi başka bir türle, hatta kendi derlemenizdeki başka bir <xref:System.Security.Permissions.ReflectionPermission> türle ilişkilendirirseniz, oluşturucu <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrak ve <xref:System.Security.Permissions.SecurityPermission> <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> bayrakla talep tesniye olur.  
  
- Dinamik yöntemi başka bir derlemede bir tür veya modülle ilişkilendirerseniz, oluşturucu iki şey ister: <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrak ve diğer modülü içeren derlemenin hibe kümesi. Diğer bir deyişle, arama yığınınız hedef modülün hibe kümesindeki <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>tüm izinleri ve .  
  
    > [!NOTE]
    > Geriye dönük uyumluluk için, hedef hibe kümesi <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> artı için talep <xref:System.Security.Permissions.SecurityPermission> başarısız <xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence?displayProperty=nameWithType> olursa, oluşturucu bayrak ile talep eder.  
  
 Bu listedeki öğeler yayan derlemenin hibe kümesi açısından açıklansa da, taleplerin uygulama etki alanı sınırı da dahil olmak üzere tam çağrı yığınına karşı yapıldığını unutmayın.  
  
 Daha fazla bilgi <xref:System.Reflection.Emit.DynamicMethod> için sınıfa bakın.  
  
### <a name="generating-dynamic-methods-from-partially-trusted-code"></a>Kısmen Güvenilen Koddan Dinamik Yöntemler Oluşturma  
  
> [!NOTE]
> Kısmen güvenilen koddan dinamik yöntemler oluşturmanın önerilen [yolu, anonim olarak barındırılan dinamik yöntemleri](#Anonymously_Hosted_Dynamic_Methods)kullanmaktır.  
  
 Internet izinleri olan bir derlemenin dinamik bir yöntem oluşturup çalıştırabileceği koşulları göz önünde bulundurun:  
  
- Dinamik yöntem, modülü ya da yayan türüyle ilişkilidir veya hibe <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> kümesi içerir ve hibe kümesi yayan derlemenin hibe kümesine eşit olan bir derlemedeki modülle veya bir alt kümesiyle ilişkilidir.  
  
- Dinamik yöntem yalnızca ortak türleri ve üyeleri kullanır. Hibe kümesi, <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> hibe kümesi yayan derlemenin hibe kümesine eşit olan bir derlemedeki bir modülü içeriyorsa ve bu modülle ilişkiliyse, ilişkili modülde (Visual `internal` `Friend` Basic'te, `assembly` ortak dilde çalışma zamanı meta verilerinde) işaretlenmiş türleri ve üyeleri kullanabilir.  
  
- Dinamik yöntem tarafından kullanılan tüm tür ve üyeler tarafından talep edilen izinler, kısmen güvenilen derlemenin hibe kümesine dahil edilir.  
  
- Dinamik yöntem JIT görünürlük denetimlerini atlamaz.  
  
> [!NOTE]
> Dinamik yöntemler hata ayıklama sembollerini desteklemez.  
  
<a name="Version_Information"></a>
## <a name="version-information"></a>Sürüm Bilgileri  
 .NET Framework 4'ten başlayarak, makine genelinde güvenlik ilkesi ortadan kaldırılır ve güvenlik saydamlığı varsayılan zorlama mekanizması haline gelir. [Bkz. Güvenlik Değişiklikleri](../security/security-changes.md).  
  
 .NET Framework 2.0 Service Pack <xref:System.Security.Permissions.ReflectionPermission> 1'den başlayarak, dinamik derlemeler ve dinamik yöntemler yayan <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> bayrak artık gerekli değildir. Bu bayrak .NET Framework'ün önceki tüm sürümlerinde gereklidir.  
  
> [!NOTE]
> <xref:System.Security.Permissions.ReflectionPermission><xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> bayrak ile varsayılan olarak `FullTrust` ve `LocalIntranet` adlandırılmış izin kümeleri dahildir, ancak `Internet` izin kümesinde değil. Bu nedenle, .NET Framework'ün önceki sürümlerinde, bir kitaplık yalnızca <xref:System.Security.PermissionSet.Assert%2A> bir <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>.'yi çalıştırırsa Internet izinleriyle kullanılabilir. Bu tür kitaplıklar, kodlama hataları güvenlik açıkları neden olabilir, çünkü dikkatli güvenlik incelemesi gerektirir. .NET Framework 2.0 SP1, kod oluşturma doğal olarak ayrıcalıklı bir işlem olmadığından, kodun herhangi bir güvenlik talebi vermeden kısmi güven senaryolarında yayımlanmasına izin verir. Diğer bir süre, oluşturulan kodun, onu yayıtan derlemeden daha fazla izini yoktur. Bu, kod yayan kitaplıkların güvenlik saydam olmasını sağlar <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>ve güvenli bir kitaplık yazma görevini basitleştiren bir türe koyma gereksinimini ortadan kaldırır.  
  
 Buna ek olarak, .NET Framework 2.0 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> SP1, kısmen güvenilen dinamik yöntemlerden herkese açık olmayan türlere ve üyelere erişmek için bayrak sunar. .NET Framework'ün önceki <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> sürümlerinde, genel olmayan türlere ve üyelere erişen dinamik yöntemler için bayrak gerekir; bu, kısmen güvenilen koda asla verilmemesi gereken bir izindir.  
  
 Son olarak, .NET Framework 2.0 SP1 anonim olarak barındırılan yöntemleri sunar.  
  
### <a name="obtaining-information-on-types-and-members"></a>Türleri ve Üyeleri Hakkında Bilgi Edinme  
 .NET Framework 2.0'dan başlayarak, genel olmayan türler ve üyeler hakkında bilgi almak için izin gerekmez. Yansıma dinamik yöntemler yontmak için gerekli bilgileri elde etmek için kullanılır. Örneğin, <xref:System.Reflection.MethodInfo> nesneler yöntem çağrıları yontmak için kullanılır. .NET Framework'ün önceki <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> sürümlerinde bayrak gerekir. Daha fazla bilgi için Yansıma [için Güvenlik Hususları'na](security-considerations-for-reflection.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansımayla İlgili Güvenlik Konuları](security-considerations-for-reflection.md)
- [Dinamik Yöntemleri ve Derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)
