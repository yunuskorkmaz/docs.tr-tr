---
title: Yansımayla İlgili Güvenlik Konuları
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], reflection
- MethodInfo parameters
- reflection, security
- partial trust,reflection
- nonpublic members
- reflection,partial trust
- link demands
ms.assetid: 42d9dc2a-8fcc-4ff3-b002-4ff260ef3dc5
ms.openlocfilehash: 1d5289ce15c213024af576c99fe039f5d6c1a247
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130065"
---
# <a name="security-considerations-for-reflection"></a>Yansımayla İlgili Güvenlik Konuları

Yansıma, türler ve Üyeler hakkında bilgi elde etme ve üyelere erişme (diğer bir deyişle, yöntem ve oluşturucuları çağırmak, olay işleyicilerini eklemek ve kaldırmak, vb.) için bilgi alma özelliği sağlar. Türler ve Üyeler hakkında bilgi edinmek için yansıma kullanımı sınırlı değildir. Tüm kod, aşağıdaki görevleri gerçekleştirmek için yansıma kullanabilir:

- Türleri ve üyeleri numaralandırın ve bunların meta verilerini inceleyin.

- Derlemeleri ve modülleri numaralandırın ve inceleyin.

Üyelere, karşıtlığa göre erişmek için yansıma kullanımı, kısıtlamalara tabidir. .NET Framework 4 ' ten başlayarak, yalnızca güvenilir kod, güvenlik açısından kritik üyelere erişmek için yansıma kullanabilir. Ayrıca, yalnızca güvenilen kod, derlenmiş kod tarafından doğrudan erişilemeyen özel üyelere erişmek için yansıma kullanabilir. Son olarak, güvenli kritik bir üyeye erişmek için yansıma kullanan kodun, derlenmiş kod ile olduğu gibi, güvenli kritik üye taleplerine göre her türlü izni olması gerekir.

Kod, gerekli izinlere bağlı olarak, aşağıdaki erişim türlerini gerçekleştirmek için yansıma kullanabilir:

- Güvenlik açısından kritik olmayan ortak üyelere erişin.

- Bu Üyeler güvenlik açısından kritik değilse, derlenmiş kod için erişilebilen özel üyelere erişin. Bu tür bir ortak üyenin örnekleri şunlardır:

  - Çağıran kodun temel sınıflarının korunan üyeleri. (Yansıma içinde bu, Aile düzeyinde erişim olarak adlandırılır.)

  - çağıran kodun derlemesinde Üyeler (Visual Basic`Friend` Üyeler) `internal`. (Yansıma içinde bu, derleme düzeyinde erişim olarak adlandırılır.)

  - Çağıran kodu içeren sınıfın diğer örneklerinin özel üyeleri.

Örneğin, bir korumalı uygulama etki alanında çalıştırılan kod, uygulama etki alanı ek izin vermediği takdirde bu listede açıklanan erişimle sınırlıdır.

.NET Framework 2,0 Service Pack 1 ' den başlayarak, normalde erişilemeyen üyelere erişmeye çalışmak, hedef nesnenin izin kümesi için bir talep oluşturur ve <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission>. Tam güvenle çalışan kod (örneğin, komut satırından başlatılan bir uygulamadaki kod) bu izinleri her zaman karşılar. (Bu makalenin ilerleyen kısımlarında açıklandığı gibi, güvenlik açısından kritik üyelere erişme kısıtlamalarına tabidir.)

İsteğe bağlı olarak, bir korumalı uygulama etki alanı, bu makalenin ilerleyen kısımlarında, [normalde erişilemeyen üyelere erişme](#accessingNormallyInaccessible)bölümünde açıklandığı gibi <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission> verebilir.

<a name="accessingSecurityCritical"></a>

## <a name="accessing-security-critical-members"></a>Güvenlik açısından kritik üyelere erişme

<xref:System.Security.SecurityCriticalAttribute>, bir üye, <xref:System.Security.SecurityCriticalAttribute>olan bir türe aitse veya güvenlik açısından kritik bir derlemede yer alıyorsa, güvenlik açısından kritik öneme sahiptir. .NET Framework 4 ' ten başlayarak, güvenlik açısından kritik üyelere erişim kuralları aşağıdaki gibidir:

- Saydam kod, kod tam güvenilir olsa bile, güvenlik açısından kritik üyelere erişmek için yansıma kullanamaz. <xref:System.MethodAccessException>, <xref:System.FieldAccessException>veya <xref:System.TypeAccessException> oluşturulur.

- Kısmi güvenle çalışan kod saydam olarak değerlendirilir.

Bu kurallar, bir güvenlik açısından kritik üyeye doğrudan derlenen kodla erişilip erişilmediği veya yansıma kullanılarak erişilen aynı.

Komut satırından çalıştırılan uygulama kodu tam güvenle çalışır. Saydam olarak işaretlenmediği sürece, güvenlik açısından kritik üyelere erişmek için yansıma kullanabilir. Aynı kod kısmi güvenle (örneğin, bir korumalı uygulama etki alanında) çalıştırıldığında, derlemenin güven düzeyi güvenlik açısından kritik koda erişip erişemeyeceğini belirler: derlemenin tanımlayıcı bir adı varsa ve genel derleme önbelleğinde yüklüyse, bu bir Güvenilen derleme ve güvenlik açısından kritik üyeleri çağırabilir. Güvenilmiyorsa, saydam olarak işaretlenmese bile saydam hale gelir ve güvenlik açısından kritik üyelere erişemez.

.NET Framework 4 ' teki güvenlik modeli hakkında daha fazla bilgi için bkz. [güvenlik değişiklikleri](../security/security-changes.md).

## <a name="reflection-and-transparency"></a>Yansıma ve saydamlık

.NET Framework 4 ' ten başlayarak, ortak dil çalışma zamanı, derlemenin güven düzeyi ve uygulama etki alanının güven düzeyi dahil olmak üzere çeşitli faktörlerden bir türün veya üyenin saydamlık düzeyini belirler. Yansıma, bir türün saydamlık düzeyini keşfetmenizi sağlamak için <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Type.IsSecuritySafeCritical%2A>ve <xref:System.Type.IsSecurityTransparent%2A> özellikleri sağlar. Aşağıdaki tabloda bu özelliklerin geçerli birleşimleri gösterilmektedir.

|Güvenlik düzeyi|IsSecurityCritical|IsSecuritySafeCritical|IsSecurityTransparent|
|--------------------|------------------------|----------------------------|---------------------------|
|Kritik|`true`|`false`|`false`|
|Güvenli kritik|`true`|`true`|`false`|
|Geçirgen|`false`|`false`|`true`|

Bu özelliklerin kullanılması, bir derlemenin ve türlerin güvenlik ek açıklamalarını inceleyerek, geçerli güven düzeyini denetleyerek ve çalışma zamanının kurallarını çoğaltmaya çalışırken çok daha basittir. Örneğin, komut satırından çalıştırıldığında aynı tür güvenlik açısından kritik veya korumalı bir uygulama etki alanında çalıştırıldığında güvenlik açısından kritik olabilir.

<xref:System.Reflection.MethodBase>, <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.Emit.TypeBuilder>, <xref:System.Reflection.Emit.MethodBuilder>ve <xref:System.Reflection.Emit.DynamicMethod> sınıflarında benzer özellikler vardır. (Diğer yansıma ve yansıma yayma soyutlamaları için, güvenlik öznitelikleri ilişkili yöntemlere uygulanır; Örneğin, özellikler söz konusu olduğunda özellik erişimcilerine uygulanırlar.)

<a name="accessingNormallyInaccessible"></a>

## <a name="accessing-members-that-are-normally-inaccessible"></a>Normalde erişilemeyen üyelere erişme

Ortak dil çalışma zamanının erişilebilirlik kurallarına göre erişilemeyen üyeleri çağırmak üzere yansıma kullanmak için, kodunuzun iki izinlerden birine verilmesi gerekir:

- Kodun herhangi bir ortak üyeyi çağırmasına izin vermek için: kodunuz <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission> verilmelidir.

  > [!NOTE]
  > Varsayılan olarak, güvenlik ilkesi Internet 'ten kaynaklanan koda yönelik bu izni reddeder. Bu izin, Internet 'ten kaynaklanan koda hiçbir şekilde verilmemelidir.

- Çağrılan üyeyi içeren derlemenin izin kümesi, çağıran kodu içeren derlemenin izin kümesi olan veya bir alt kümesiyle aynı olduğu sürece kodun tüm ortak üyeleri çağırmasına izin vermek için: kodunuz <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission> verilmelidir.

Örneğin, <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağıyla bir uygulama etki alanı Internet izinleri <xref:System.Security.Permissions.ReflectionPermission> ve ardından iki derleme ile bir Internet uygulaması (A ve B) verdiğinizi varsayalım.

- Derleme A, derleme b 'nin izin kümesi, bir izin verilmeyen hiçbir izinleri içermediğinden, derleme B 'nin özel üyelerine erişmek için yansımayı kullanabilir.

- Derleme A, mscorlib. dll gibi .NET Framework derlemelerin özel üyelerine erişmek için yansıma kullanamaz, çünkü mscorlib. dll tam olarak güvenilirdir ve bu nedenle A derlemesine verilmemiş izinlere sahiptir. Kod erişim güvenliği yığına çalışma zamanında yol gösterecektir <xref:System.MemberAccessException> oluşur.

## <a name="serialization"></a>Serileştirme

Serileştirme için, <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.SecurityPermission>, erişilebilirliği ne olursa olsun seri hale getirilebilir türlerin üyelerini alma ve ayarlama yeteneği sağlar. Bu izin, kodun bir örneğin özel durumunu bulmasını ve değiştirmesini sağlar. (Uygun izinlerin verilmesinin yanı sıra, türün meta verilerde seri hale getirilebilir olarak [işaretlenmesi](../../standard/attributes/applying-attributes.md) gerekir.)

## <a name="parameters-of-type-methodinfo"></a>MethodInfo türünde parametreler

Özellikle güvenilen kod için <xref:System.Reflection.MethodInfo> parametreleri alan genel üyelerin yazılmasından kaçının. Bu tür Üyeler kötü amaçlı koda karşı daha savunmasız olabilir. Örneğin, bir <xref:System.Reflection.MethodInfo> parametresi alan, yüksek oranda güvenilen kodda ortak bir üyeyi göz önünde bulundurun. Ortak üyenin, sağlanan parametrede <xref:System.Reflection.MethodBase.Invoke%2A> yöntemini dolaylı olarak çağırdığını varsayın. Ortak üye gerekli izin denetimlerini gerçekleştirmiyorsa, güvenlik sistemi çağıranın son derece güvenilir olduğunu belirlediği için <xref:System.Reflection.MethodBase.Invoke%2A> yöntemine yapılan çağrı her zaman başarılı olur. Kötü amaçlı kodun yöntemi doğrudan çağırmak için izni olmasa bile, ortak üyeyi çağırarak dolaylı olarak bu şekilde devam edebilir.

## <a name="version-information"></a>Sürüm Bilgileri

- .NET Framework 4 ' ten başlayarak saydam kod, güvenlik açısından kritik üyelere erişmek için yansıma kullanamaz.

- <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağı, .NET Framework 2,0 hizmet paketi 1 ' de kullanıma sunulmuştur. .NET Framework önceki sürümleri, Özel üyelere erişmek için yansıma kullanan kod için <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağını gerektirir. Bu, kısmen güvenilen koda asla verilmemesi gereken bir izindir.

- .NET Framework 2,0 ' den başlayarak, özel türler hakkında bilgi edinmek için yansıma kullanımı ve Üyeler herhangi bir izin gerektirmez. Önceki sürümlerde, <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> bayrağıyla <xref:System.Security.Permissions.ReflectionPermission> gereklidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.ReflectionPermissionFlag>
- <xref:System.Security.Permissions.ReflectionPermission>
- <xref:System.Security.Permissions.SecurityPermission>
- [Güvenlik Değişiklikleri](../security/security-changes.md)
- [Kod erişim güvenliği](../misc/code-access-security.md)
- [Yansıma Yaymadaki Güvenlik Sorunları](security-issues-in-reflection-emit.md)
- [Tür Bilgilerini Görüntüleme](viewing-type-information.md)
- [Öznitelikleri Uygulama](../../standard/attributes/applying-attributes.md)
- [Özel Özniteliklere Erişim](accessing-custom-attributes.md)
