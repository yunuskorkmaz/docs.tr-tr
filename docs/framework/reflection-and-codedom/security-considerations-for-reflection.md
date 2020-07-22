---
title: Yansımayla İlgili Güvenlik Konuları
description: .NET ' te yansımaya yönelik güvenlik konuları hakkında bilgi edinin. Türler ve Üyeler hakkında bilgi almak için izin verilir, ancak üyelere erişmek için kısıtlamalar vardır.
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
ms.openlocfilehash: 0465cbd5ceb7d4f44bb6d10865fcbd17b8ed7af6
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865261"
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

  - `internal``Friend`çağıran kodun derlemesindeki Üyeler (Visual Basic Üyeler). (Yansıma içinde bu, derleme düzeyinde erişim olarak adlandırılır.)

  - Çağıran kodu içeren sınıfın diğer örneklerinin özel üyeleri.

Örneğin, bir korumalı uygulama etki alanında çalıştırılan kod, uygulama etki alanı ek izin vermediği takdirde bu listede açıklanan erişimle sınırlıdır.

.NET Framework 2,0 Service Pack 1 ' den başlayarak, normalde erişilemeyen üyelere erişmeye çalışmak, hedef nesnenin izin kümesi ve bayrağıyla birlikte bir talep oluşturur <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> . Tam güvenle çalışan kod (örneğin, komut satırından başlatılan bir uygulamadaki kod) bu izinleri her zaman karşılar. (Bu makalenin ilerleyen kısımlarında açıklandığı gibi, güvenlik açısından kritik üyelere erişme kısıtlamalarına tabidir.)

İsteğe bağlı olarak, <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> Bu makalenin ilerleyen kısımlarında, [normalde erişilemeyen üyelere erişme](#accessingNormallyInaccessible)bölümünde açıklandığı gibi, korumalı bir uygulama etki alanı bayrağa izin verebilir.

<a name="accessingSecurityCritical"></a>

## <a name="accessing-security-critical-members"></a>Güvenlik açısından kritik üyelere erişme

Bir üye, ' a sahip <xref:System.Security.SecurityCriticalAttribute> olan bir türe aitse <xref:System.Security.SecurityCriticalAttribute> veya güvenlik açısından kritik bir derlemede yer alıyorsa, güvenlik açısından kritik öneme sahiptir. .NET Framework 4 ' ten başlayarak, güvenlik açısından kritik üyelere erişim kuralları aşağıdaki gibidir:

- Saydam kod, kod tam güvenilir olsa bile, güvenlik açısından kritik üyelere erişmek için yansıma kullanamaz. <xref:System.MethodAccessException>, <xref:System.FieldAccessException> Veya <xref:System.TypeAccessException> oluşturulur.

- Kısmi güvenle çalışan kod saydam olarak değerlendirilir.

Bu kurallar, bir güvenlik açısından kritik üyeye doğrudan derlenen kodla erişilip erişilmediği veya yansıma kullanılarak erişilen aynı.

Komut satırından çalıştırılan uygulama kodu tam güvenle çalışır. Saydam olarak işaretlenmediği sürece, güvenlik açısından kritik üyelere erişmek için yansıma kullanabilir. Aynı kod kısmi güvenle çalıştırıldığında (örneğin, bir korumalı uygulama etki alanında), derlemenin güven düzeyi, güvenlik açısından kritik koda erişip erişemeyeceğini belirler: derlemenin tanımlayıcı bir adı varsa ve genel derleme önbelleğinde yüklüyse, bu güvenilir bir derlemedir ve güvenlik açısından kritik üyeleri çağırabilir. Güvenilmiyorsa, saydam olarak işaretlenmese bile saydam hale gelir ve güvenlik açısından kritik üyelere erişemez.

.NET Framework 4 ' teki güvenlik modeli hakkında daha fazla bilgi için bkz. [güvenlik değişiklikleri](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).

## <a name="reflection-and-transparency"></a>Yansıma ve saydamlık

.NET Framework 4 ' ten başlayarak, ortak dil çalışma zamanı, derlemenin güven düzeyi ve uygulama etki alanının güven düzeyi dahil olmak üzere çeşitli faktörlerden bir türün veya üyenin saydamlık düzeyini belirler. Yansıma, <xref:System.Type.IsSecurityCritical%2A> <xref:System.Type.IsSecuritySafeCritical%2A> <xref:System.Type.IsSecurityTransparent%2A> bir türün saydamlık düzeyini bulmanızı sağlamak için, ve özelliklerini sağlar. Aşağıdaki tabloda bu özelliklerin geçerli birleşimleri gösterilmektedir.

|Güvenlik düzeyi|IsSecurityCritical|IsSecuritySafeCritical|IsSecurityTransparent|
|--------------------|------------------------|----------------------------|---------------------------|
|Kritik|`true`|`false`|`false`|
|Güvenli kritik|`true`|`true`|`false`|
|Geçirgen|`false`|`false`|`true`|

Bu özelliklerin kullanılması, bir derlemenin ve türlerin güvenlik ek açıklamalarını inceleyerek, geçerli güven düzeyini denetleyerek ve çalışma zamanının kurallarını çoğaltmaya çalışırken çok daha basittir. Örneğin, komut satırından çalıştırıldığında aynı tür güvenlik açısından kritik veya korumalı bir uygulama etki alanında çalıştırıldığında güvenlik açısından kritik olabilir.

,,, <xref:System.Reflection.MethodBase> <xref:System.Reflection.FieldInfo> <xref:System.Reflection.Emit.TypeBuilder> <xref:System.Reflection.Emit.MethodBuilder> Ve <xref:System.Reflection.Emit.DynamicMethod> sınıflarında benzer özellikler vardır. (Diğer yansıma ve yansıma yayma soyutlamaları için, güvenlik öznitelikleri ilişkili yöntemlere uygulanır; Örneğin, özellikler söz konusu olduğunda özellik erişimcilerine uygulanırlar.)

<a name="accessingNormallyInaccessible"></a>

## <a name="accessing-members-that-are-normally-inaccessible"></a>Normalde erişilemeyen üyelere erişme

Ortak dil çalışma zamanının erişilebilirlik kurallarına göre erişilemeyen üyeleri çağırmak üzere yansıma kullanmak için, kodunuzun iki izinlerden birine verilmesi gerekir:

- Kodun herhangi bir ortak üyeyi çağırmasına izin vermek için: kodunuz <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağıyla verilmelidir.

  > [!NOTE]
  > Varsayılan olarak, güvenlik ilkesi Internet 'ten kaynaklanan koda yönelik bu izni reddeder. Bu izin, Internet 'ten kaynaklanan koda hiçbir şekilde verilmemelidir.

- Çağrılan üyeyi içeren derlemenin izin kümesi, çağıran kodu içeren derlemenin izin kümesi ile aynı veya bir alt kümesiyle aynı olduğu sürece kodun herhangi bir ortak üyeyi çağırmasına izin vermek için: kodunuz <xref:System.Security.Permissions.ReflectionPermission> bayrağıyla birlikte verilmelidir <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> .

Örneğin, bayrağını içeren bir uygulama etki alanı Internet izinleri <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> ve sonra iki derleme Ile bir Internet uygulaması (A ve B) ayarladığınızı varsayalım.

- Derleme A, derleme b 'nin izin kümesi, bir izin verilmeyen hiçbir izinleri içermediğinden, derleme B 'nin özel üyelerine erişmek için yansımayı kullanabilir.

- Derleme A, mscorlib.dll gibi .NET Framework derlemelerin özel üyelerine erişmek için yansıma kullanamaz, çünkü mscorlib.dll tamamen güvenilirdir ve bu nedenle A derlemesine verilmemiş izinlere sahiptir. <xref:System.MemberAccessException>Kod erişim güvenliği yığına çalışma zamanında yol gösterecektir bir oluşturulur.

## <a name="serialization"></a>Serileştirme

Serileştirme için, <xref:System.Security.Permissions.SecurityPermission> bayrağı ile,, <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A?displayProperty=nameWithType> Erişilebilirlik ' in ne olursa olsun, seri hale getirilebilir türlerin üyelerini alma ve ayarlama yeteneği sağlar. Bu izin, kodun bir örneğin özel durumunu bulmasını ve değiştirmesini sağlar. (Uygun izinlerin verilmesinin yanı sıra, türün meta verilerde seri hale getirilebilir olarak [işaretlenmesi](../../standard/attributes/applying-attributes.md) gerekir.)

## <a name="parameters-of-type-methodinfo"></a>MethodInfo türünde parametreler

Özellikle güvenilen kod için parametre alan genel üyelerin yazılmasından kaçının <xref:System.Reflection.MethodInfo> . Bu tür Üyeler kötü amaçlı koda karşı daha savunmasız olabilir. Örneğin, bir parametre alan, yüksek oranda güvenilen kodda ortak bir üyeyi göz önünde bulundurun <xref:System.Reflection.MethodInfo> . Ortak üyenin, <xref:System.Reflection.MethodBase.Invoke%2A> yöntemi sağlanan parametrede dolaylı olarak çağırdığını varsayın. Ortak üye gerekli izin denetimlerini gerçekleştirmiyorsa, <xref:System.Reflection.MethodBase.Invoke%2A> güvenlik sistemi çağıranın son derece güvenilir olduğunu belirlediği için yönteme yapılan çağrı her zaman başarılı olur. Kötü amaçlı kodun yöntemi doğrudan çağırmak için izni olmasa bile, ortak üyeyi çağırarak dolaylı olarak bu şekilde devam edebilir.

## <a name="version-information"></a>Sürüm Bilgileri

- .NET Framework 4 ' ten başlayarak saydam kod, güvenlik açısından kritik üyelere erişmek için yansıma kullanamaz.

- <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>Bayrak, .NET Framework 2,0 hizmet paketi 1 ' de kullanıma sunulmuştur. .NET Framework önceki sürümleri, <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> Özel üyelere erişmek için yansıma kullanan kod için bayrak gerektirir. Bu, kısmen güvenilen koda asla verilmemesi gereken bir izindir.

- .NET Framework 2,0 ' den başlayarak, özel türler hakkında bilgi edinmek için yansıma kullanımı ve Üyeler herhangi bir izin gerektirmez. Önceki sürümlerde, <xref:System.Security.Permissions.ReflectionPermission> <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> bayrağı gereklidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.ReflectionPermissionFlag>
- <xref:System.Security.Permissions.ReflectionPermission>
- <xref:System.Security.Permissions.SecurityPermission>
- [Güvenlik Değişiklikleri](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
- [Kod Erişimi Güvenliği](../misc/code-access-security.md)
- [Yansıma Yaymadaki Güvenlik Sorunları](security-issues-in-reflection-emit.md)
- [Tür Bilgilerini Görüntüleme](viewing-type-information.md)
- [Öznitelikleri Uygulama](../../standard/attributes/applying-attributes.md)
- [Özel Özniteliklere Erişim](accessing-custom-attributes.md)
