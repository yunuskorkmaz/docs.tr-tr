---
title: Güvenliği Saydam Kod, 2. Düzey
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 12e991e4977b0866343158c05681ddf4bd0c869b
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645728"
---
# <a name="security-transparent-code-level-2"></a>Güvenliği Saydam Kod, 2. Düzey

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Düzey 2 saydamlığı .NET Framework 4'te tanıtıldı. Bu modelin üç ilkeleri saydam kod, güvenlik açısından kritik kod ve güvenlik açısından kritik kodvardır.

- Tam güven olarak çalışan kod da dahil olmak üzere saydam kod, diğer saydam kodu veya yalnızca güvenlik açısından kritik kodu çağırabilir. Yalnızca etki alanının kısmi güven izin kümesi tarafından izin verilen eylemleri gerçekleştirebilir (varsa). Saydam kod aşağıdakileri yapamaz:

  - Ayrıcalık <xref:System.Security.CodeAccessPermission.Assert%2A> veya yükseklik gerçekleştirin.

  - Güvenli olmayan veya doğrulanamayan kod içerir.

  - Doğrudan kritik kodu arayın.

  - Öznitelik içeren <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> yerel kodu veya kodu arayın.

  - Bir <xref:System.Security.Permissions.SecurityAction.LinkDemand>. tarafından korunan bir üyeyi arayın

  - Kritik türlerden devralma.

  Buna ek olarak, saydam yöntemler kritik sanal yöntemleri geçersiz kılamaz veya kritik arabirim yöntemleri uygulayamaz.

- Güvenli kritik kod tamamen güvenilirdir, ancak saydam kod tarafından çağrılabilir. Tam güven kodunun sınırlı bir yüzey alanını ortaya çıkarır; doğruluk ve güvenlik doğrulamaları güvenli kritik kodda gerçekleşir.

- Güvenlik açısından kritik kod herhangi bir kodu arayabilir ve tam olarak güvenilirdir, ancak saydam kod la çağrılabilir.

## <a name="usage-examples-and-behaviors"></a>Kullanım Örnekleri ve Davranışlar

.NET Framework 4 kurallarını (düzey 2 saydamlığı) belirtmek için, bir derleme için aşağıdaki ek açıklamayı kullanın:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

.NET Framework 2.0 kurallarına (düzey 1 saydamlığı) kilitlemek için aşağıdaki ek açıklamayı kullanın:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

Bir derlemeye açıklama yapmazsanız, .NET Framework 4 kuralları varsayılan olarak kullanılır. Ancak, önerilen en iyi yöntem <xref:System.Security.SecurityRulesAttribute> varsayılanbağlı yerine öznitelik kullanmaktır.

### <a name="assembly-wide-annotation"></a>Montaj genelinde Ek Açıklama

Aşağıdaki kurallar derleme düzeyinde özniteliklerin kullanımı için geçerlidir:

- Öznitelik belirtmezseniz: Herhangi bir öznitelik belirtmezseniz, çalışma zamanı, güvenlik açısından kritik olmanın bir devralma kuralını ihlal ettiği durumlar (örneğin, saydam bir sanal veya arabirim yöntemini geçersiz kıldığı veya uygularken) dışında tüm kodu güvenlik açısından kritik olarak yorumlar. Bu gibi durumlarda, yöntemler güvenli-kritik. Hiçbir öznitelik belirtme, sizin için saydamlık kurallarını belirlemek için ortak dil çalışma süresineden olur.

- `SecurityTransparent`: Tüm kod saydamdır; tüm derleme ayrıcalıklı veya güvensiz bir şey yapmaz.

- `SecurityCritical`: Bu derlemedeki türler tarafından getirilen tüm kodlar önemlidir; diğer tüm kod saydamdır. Bu senaryo, herhangi bir öznitelik belirtmemeye benzer; ancak, ortak dil çalışma süresi saydamlık kurallarını otomatik olarak belirlemez. Örneğin, sanal veya soyut bir yöntemi geçersiz kılarsanız veya varsayılan olarak bir arabirim yöntemi uygularsanız, bu yöntem saydamdır. Yöntemi açıkça açıklama olarak veya; `SecurityCritical` `SecuritySafeCritical` aksi takdirde, yük zamanında bir atılmalıdır. <xref:System.TypeLoadException> Bu kural, hem taban sınıf hem de türemiş sınıf aynı derlemede olduğunda da geçerlidir.

- `AllowPartiallyTrustedCallers`(yalnızca düzey 2): Tüm kod varsayılan olarak saydamdır. Ancak, tek tek türleri ve üyeleri başka öznitelikleri olabilir.

Aşağıdaki tablo, Düzey 2 için derleme düzeyi davranışını Düzey 1 ile karşılaştırır.

|Montaj özniteliği|Düzey 2|Düzey 1|
|------------------------|-------------|-------------|
|Kısmen güvenilen bir derlemede öznitelik yok|Türler ve üyeler varsayılan olarak saydamdır, ancak güvenlik açısından kritik veya güvenlik açısından güvenli kritik olabilir.|Tüm tür ve üyeler saydamdır.|
|Öznitelik yok|Hiçbir öznitelik belirtme, sizin için saydamlık kurallarını belirlemek için ortak dil çalışma süresineden olur. Güvenlik açısından kritik olan ın bir devralma kuralını ihlal ettiği durumlar dışında, tüm türler ve üyeler güvenlik açısından önemlidir.|Tam olarak güvenilen bir derlemede (genel montaj önbelleğinde veya tam güven olarak `AppDomain`tanımlanır) tüm türler saydamdır ve tüm üyeler güvenlik açısından kritik öneme sahiptir.|
|`SecurityTransparent`|Tüm tür ve üyeler saydamdır.|Tüm tür ve üyeler saydamdır.|
|`SecurityCritical(SecurityCriticalScope.Everything)`|Geçerli değildir.|Tüm türler ve üyeler güvenlik açısından kritik öneme sahiptir.|
|`SecurityCritical`|Bu derlemedeki türler tarafından tanıtılan tüm kod lar önemlidir; diğer tüm kod saydamdır. Sanal veya soyut bir yöntemi geçersiz kılarsanız veya bir arabirim yöntemi uygularsanız, metodu açıkça `SecurityCritical` "veya `SecuritySafeCritical`.|Tüm kod varsayılan olarak saydamdır. Ancak, tek tek türleri ve üyeleri başka öznitelikleri olabilir.|

### <a name="type-and-member-annotation"></a>Tür ve Üye Ek Açıklaması

Bir türe uygulanan güvenlik öznitelikleri, tür tarafından tanıtılan üyeler için de geçerlidir. Ancak, temel sınıf veya arabirim uygulamalarının sanal veya soyut geçersiz kılmaları için geçerli değildir. Aşağıdaki kurallar, özniteliklerin tür ve üye düzeyinde kullanımı için geçerlidir:

- `SecurityCritical`: Tür veya üye önemlidir ve yalnızca tam güven koduyla çağrılabilir. Güvenlik açısından kritik bir türde tanıtılan yöntemler önemlidir.

    > [!IMPORTANT]
    > Temel sınıflara veya arabirimlere getirilen ve güvenlik açısından kritik bir sınıfta geçersiz kılınan veya uygulanan sanal ve soyut yöntemler varsayılan olarak saydamdır. Ya da `SecuritySafeCritical` `SecurityCritical`.

- `SecuritySafeCritical`: Türü veya üyesi güvenli kritik. Ancak, tür veya üye saydam (kısmen güvenilen) koddan çağrılabilir ve diğer kritik kodlar kadar yeteneklidir. Kod güvenlik için denetlenmelidir.

## <a name="override-patterns"></a>Desenleri Geçersiz Kılma

Aşağıdaki tablo, düzey 2 saydamlığı için izin verilen yöntemi geçersiz kılar.

|Temel sanal/arayüz üyesi|Geçersiz kılma/arabirim|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a>Devralma Kuralları

Bu bölümde, erişim ve yeteneklere `Critical`göre `SafeCritical` aşağıdaki sıra , ve koda `Transparent`atanır:

`Transparent` < `SafeCritical` < `Critical`

- Türleri için kurallar: Soldan sağa gitmek, erişim daha kısıtlayıcı hale gelir. Türetilen türler en az temel tür kadar kısıtlayıcı olmalıdır.

- Yöntem kuralları: Türemiş yöntemler temel yöntemden erişilebilirliği değiştiremez. Varsayılan davranış için açıklamalı olmayan tüm türemiş yöntemler. `Transparent` Geçersiz türlerin türevleri, geçersiz kılınan yöntem açıkça 'olarak `SecurityCritical`açıklanmazsa, bir özel durum atılmasına neden olur.

Aşağıdaki tablo, izin verilen tür devralma desenleri gösterir.

|Taban sınıf|Türemiş sınıf olabilir|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

Aşağıdaki tabloda izin verilmeyen tür devralma desenleri gösterilmektedir.

|Taban sınıf|Türetilmiş sınıf olamaz|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

Aşağıdaki tabloda izin verilen yöntem kalıtım desenleri gösterilmektedir.

|Temel yöntem|Türemiş yöntem,|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

Aşağıdaki tabloda izin verilmeyen yöntem kalıtım desenleri gösterilmektedir.

|Temel yöntem|Türemiş yöntem,|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> Bu devralma kuralları düzey 2 türleri ve üyeleri için geçerlidir. Düzey 1 derlemeleri türleri düzey 2 güvenlik açısından kritik türleri ve üyeleri devralabilir. Bu nedenle, düzey 2 türleri ve üyeleri seviye 1 mirasçılar için ayrı miras talepleri olmalıdır.

## <a name="additional-information-and-rules"></a>Ek Bilgiler ve Kurallar

### <a name="linkdemand-support"></a>LinkDemand Desteği

Düzey 2 saydamlık modeli <xref:System.Security.Permissions.SecurityAction.LinkDemand> <xref:System.Security.SecurityCriticalAttribute> öznitelik ile değiştirir. Eski (düzey 1) kodunda, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> otomatik <xref:System.Security.Permissions.SecurityAction.Demand>olarak bir .

### <a name="reflection"></a>Yansıma

Kritik bir yöntem çağırmak veya kritik bir alanı okumak tam güven talebini tetikler (tıpkı özel bir yöntem veya alanı çağrıştırıyormuşgibi). Bu nedenle, tam güven kodu kritik bir yöntem çağırabilir, kısmi güven kodu ise.

<xref:System.Reflection> Türü, `SecurityCritical`yöntemi veya alanı , `SecuritySafeCritical`, , , `SecurityTransparent` <xref:System.Type.IsSecurityCritical%2A> <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, , ve <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Öznitelik varlığını denetlemek yerine yansımayı kullanarak saydamlığı belirlemek için bu özellikleri kullanın. Saydamlık kuralları karmaşıktır ve öznitelik için denetleme yeterli olmayabilir.

> [!NOTE]
> Bir `SafeCritical` yöntem `true` hem <xref:System.Type.IsSecurityCritical%2A> <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>de `SafeCritical` , çünkü gerçekten kritik (kritik kod olarak aynı özelliklere sahiptir, ancak saydam kod dan çağrılabilir) için döndürür.

Dinamik yöntemler, bağlı oldukları modüllerin saydamlıklarını devralır; türün saydamlığı (bir türe bağlıysalar) devralınmaz.

### <a name="skip-verification-in-full-trust"></a>Tam Güven İçinde Doğrulamayı Atlama

Özelliği öznitelikte ayarlayarak tam güvenilen <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> saydam `true` derlemeler için doğrulamayı <xref:System.Security.SecurityRulesAttribute> atlayabilirsiniz:

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

Özellik <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> varsayılan `false` olarak dır, bu nedenle `true` özelliğin doğrulamayı atlamak için ayarlanması gerekir. Bu sadece optimizasyon amaçlı yapılmalıdır. `transparent` [PEVerify aracındaki](../tools/peverify-exe-peverify-tool.md)seçeneği kullanarak derlemedeki saydam kodun doğrulanabilir olduğundan emin olmalısınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik-Saydam Kod, Düzey 1](security-transparent-code-level-1.md)
- [Güvenlik Değişiklikleri](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
