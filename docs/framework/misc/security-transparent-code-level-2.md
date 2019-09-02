---
title: Güvenliği Saydam Kod, 2. Düzey
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61a436efe3e3af7ce4aa50afe242838b1cd8941e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206074"
---
# <a name="security-transparent-code-level-2"></a>Güvenliği Saydam Kod, 2. Düzey

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Düzey 2 saydamlık .NET Framework 4 ' te tanıtılmıştı. Bu modelin üç listesi saydam kod, güvenli güvenlik açısından kritik kod ve güvenlik açısından kritik koddur.

- Tam güven olarak çalışan kod dahil saydam kod, yalnızca diğer saydam kodu veya güvenlik açısından güvenli kritik kodu çağırabilir. Yalnızca etki alanının kısmi güven izin kümesi (varsa) tarafından izin verilen eylemleri gerçekleştirebilir. Saydam kod şunları yapılamıyor:

  - Bir <xref:System.Security.CodeAccessPermission.Assert%2A> ayrıcalık yükselmesi veya yükseltmesi gerçekleştirin.

  - Güvenli olmayan veya doğrulanamayan kod içeriyor.

  - Kritik kodu doğrudan çağırın.

  - Yerel kodu veya kodu <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliğiyle çağırın.

  - Tarafından korunan bir üyeyi çağırın <xref:System.Security.Permissions.SecurityAction.LinkDemand>.

  - Kritik türlerden devralma.

  Ayrıca, saydam Yöntemler kritik sanal yöntemleri geçersiz kılamaz veya kritik arabirim yöntemleri uygulayamaz.

- Güvenli kritik kod tamamen güvenilirdir, ancak saydam kod tarafından çağrılabilir. Tam güven kodunun sınırlı bir yüzey alanını kullanıma sunar; güvenli kritik kodda doğruluk ve güvenlik doğrulamaları meydana gelir.

- Güvenlik açısından kritik kod herhangi bir kodu çağırabilir ve tamamen güvenilirdir, ancak saydam kod tarafından çağrılamaz.

Bu konu aşağıdaki bölümleri içermektedir:

- [Kullanım örnekleri ve davranışlar](#examples)

- [Geçersiz kılma desenleri](#override)

- [Devralma kuralları](#inheritance)

- [Ek bilgi ve kurallar](#additional)

<a name="examples"></a>

## <a name="usage-examples-and-behaviors"></a>Kullanım Örnekleri ve Davranışlar

.NET Framework 4 kuralları belirtmek için (düzey 2 saydamlık), bir derleme için aşağıdaki ek açıklamayı kullanın:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

.NET Framework 2,0 kurallarına (düzey 1 saydamlık) kilitlemek için aşağıdaki ek açıklamayı kullanın:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

Bir derlemeye Not eklemek istemiyorsanız, varsayılan olarak .NET Framework 4 kuralları kullanılır. Ancak önerilen en iyi yöntem, varsayılan değere göre değil <xref:System.Security.SecurityRulesAttribute> , özniteliğini kullanmaktır.

### <a name="assembly-wide-annotation"></a>Bütünleştirilmiş kod genelinde ek açıklama

Aşağıdaki kurallar, derleme düzeyinde özniteliklerin kullanımı için geçerlidir:

- Öznitelik yok: Herhangi bir öznitelik belirtmezseniz, çalışma zamanı tüm kodu güvenlik açısından kritik olarak yorumlar ve güvenlik açısından kritik olduğu durumlar dışında, bir devralma kuralını ihlal ediyor (örneğin, bir saydam sanal veya arabirim yöntemi geçersiz kılırken veya uygularken). Bu durumlarda, Yöntemler güvenli öneme sahiptir. Hiçbir öznitelik belirtilmesi, ortak dil çalışma zamanının sizin için saydamlık kurallarını belirlemesine neden olur.

- `SecurityTransparent`: Tüm kod saydamdır; Tüm derleme ayrıcalıklı veya güvenli olmayan hiçbir işlem yapmaz.

- `SecurityCritical`: Bu derlemedeki türler tarafından tanıtılan tüm kodlar kritiktir; diğer tüm kodlar saydamdır. Bu senaryo herhangi bir öznitelik Belirtmemeye benzer; Ancak, ortak dil çalışma zamanı, saydamlık kurallarını otomatik olarak belirleyemez. Örneğin, bir sanal veya soyut yöntemi geçersiz kılarsınız veya bir arabirim yöntemi uygularsanız, varsayılan olarak bu yöntem saydamdır. Yöntemine `SecurityCritical` açıkçaAçıklama<xref:System.TypeLoadException> eklemek zorundasınız ;Aksitakdirde,yüklemezamanındabiroluşturulur.`SecuritySafeCritical` Bu kural, hem temel sınıf hem de türetilmiş sınıf aynı derlemede olduğunda da geçerlidir.

- `AllowPartiallyTrustedCallers`(yalnızca düzey 2): Tüm kod varsayılan olarak saydam olur. Ancak, ayrı türler ve üyelerin diğer öznitelikleri olabilir.

Aşağıdaki tabloda düzey 1 düzeyi 2 için derleme düzeyi davranışı karşılaştırılmaktadır.

|Derleme özniteliği|Düzey 2|Düzey 1|
|------------------------|-------------|-------------|
|Kısmen güvenilen bir derlemede öznitelik yok|Türler ve Üyeler varsayılan olarak saydamdır, ancak güvenlik açısından kritik veya güvenlik açısından kritik öneme sahip olabilir.|Tüm türler ve Üyeler saydamdır.|
|Öznitelik yok|Hiçbir öznitelik belirtilmesi, ortak dil çalışma zamanının sizin için saydamlık kurallarını belirlemesine neden olur. Güvenlik açısından kritik olduğu durumlar dışında, bir devralma kuralını ihlal ettiğinden, tüm türler ve Üyeler güvenlik açısından kritik öneme sahiptir.|Tam güvenilir bir derlemede (genel derleme önbelleğinde veya ' de `AppDomain`tam güven olarak tanımlanır) tüm türler saydamdır ve tüm Üyeler güvenlik açısından güvenlidir.|
|`SecurityTransparent`|Tüm türler ve Üyeler saydamdır.|Tüm türler ve Üyeler saydamdır.|
|`SecurityCritical(SecurityCriticalScope.Everything)`|Geçerli değildir.|Tüm türler ve Üyeler güvenlik açısından kritik öneme sahiptir.|
|`SecurityCritical`|Bu derlemedeki türler tarafından tanıtılan tüm kodlar kritiktir; diğer tüm kodlar saydamdır. Bir sanal veya soyut yöntemi geçersiz kılarsınız veya bir arabirim yöntemi uygularsanız, yöntemi veya `SecurityCritical` `SecuritySafeCritical`olarak açıkça not almanız gerekir.|Tüm kod varsayılan olarak saydam olur. Ancak, ayrı türler ve üyelerin diğer öznitelikleri olabilir.|

### <a name="type-and-member-annotation"></a>Tür ve Üye Ek Açıklaması

Bir türe uygulanan güvenlik öznitelikleri, türü tarafından tanıtılan Üyeler için de geçerlidir. Ancak, temel sınıfın veya arabirim uygulamalarının sanal veya soyut geçersiz kılmaları için uygulanmazlar. Aşağıdaki kurallar, tür ve üye düzeyinde özniteliklerin kullanımı için geçerlidir:

- `SecurityCritical`: Tür veya üye kritiktir ve yalnızca tam güven kodu tarafından çağrılabilir. Güvenlik açısından kritik bir tür içinde sunulan yöntemler kritiktir.

    > [!IMPORTANT]
    > Temel sınıflarda veya arabirimlerde tanıtılan ve güvenlik açısından kritik bir sınıfta geçersiz kılınan veya uygulanan sanal ve soyut yöntemler varsayılan olarak saydamdır. `SecuritySafeCritical` Ya`SecurityCritical`da olarak tanımlanmaları gerekir.

- `SecuritySafeCritical`: Tür veya üye güvenli kritik öneme sahiptir. Ancak, tür veya üye saydam (kısmen güvenilir) koddan çağrılabilir ve diğer kritik kodlar gibi olabilir. Kod güvenlik için denetlenmelidir.

[Başa dön](#top)

<a name="override"></a>

## <a name="override-patterns"></a>Desenleri Geçersiz Kılma

Aşağıdaki tabloda düzey 2 saydamlığına izin verilen yöntem geçersiz kılmaları gösterilmektedir.

|Taban sanal/arabirim üyesi|Geçersiz kılma/arabirim|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

[Başa dön](#top)

<a name="inheritance"></a>

## <a name="inheritance-rules"></a>Devralma Kuralları

Bu bölümde, erişim ve yeteneklere göre aşağıdaki sıra `Transparent`, `Critical`ve `SafeCritical` koduna atanır:

`Transparent` < `SafeCritical` < `Critical`

- Türlerin kuralları: Soldan sağa doğru gidip erişim daha kısıtlayıcı hale gelir. Türetilmiş türler, temel tür olarak en az kısıtlayıcı olmalıdır.

- Yöntemler için kurallar: Türetilmiş yöntemler, taban yönteminden erişilebilirliği değiştiremezler. Varsayılan davranış için, açıklama eklenmiş olmayan tüm türetilmiş yöntemler vardır `Transparent`. Kritik türlerin türettiği, geçersiz kılınan yöntemin olarak `SecurityCritical`açıkça açıklanmadığı durumlarda bir özel durumun oluşturulmasına neden olur.

Aşağıdaki tabloda, izin verilen tür devralma desenleri gösterilmektedir.

|Temel sınıf|Türetilmiş sınıf|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

Aşağıdaki tabloda izin verilmeyen tür devralma desenleri gösterilmektedir.

|Temel sınıf|Türetilmiş sınıf olamaz|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

Aşağıdaki tabloda izin verilen yöntem devralma desenleri gösterilmektedir.

|Base yöntemi|Türetilmiş yöntem şu şekilde olabilir|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

Aşağıdaki tabloda izin verilmeyen Yöntem devralma desenleri gösterilmektedir.

|Base yöntemi|Türetilmiş yöntem olamaz|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> Bu devralma kuralları, düzey 2 türleri ve üyeleri için geçerlidir. Düzey 1 derlemelerdeki türler, düzey 2 güvenlik açısından kritik türlerden ve üyelerden devralınabilir. Bu nedenle, düzey 2 türleri ve üyeleri, düzey 1 ınheritörler için ayrı devralma taleplerine sahip olmalıdır.

[Başa dön](#top)

<a name="additional"></a>

## <a name="additional-information-and-rules"></a>Ek Bilgiler ve Kurallar

### <a name="linkdemand-support"></a>LinkDemand Desteği

Düzey 2 saydamlık modeli, <xref:System.Security.Permissions.SecurityAction.LinkDemand> <xref:System.Security.SecurityCriticalAttribute> öğesinin özniteliğiyle değiştirilir. Eski (düzey 1) kodda, bir <xref:System.Security.Permissions.SecurityAction.LinkDemand> otomatik olarak bir <xref:System.Security.Permissions.SecurityAction.Demand>olarak değerlendirilir.

### <a name="reflection"></a>Yansıma

Kritik bir yöntemi çağırmak veya kritik bir alanı okumak, tam güven için bir talep tetikler (özel bir yöntem veya alan çağırmak gibi). Bu nedenle, tam güven kodu kritik bir yöntemi çağırabilir, ancak kısmi güven kodu olamaz.

Türü <xref:System.Reflection> , yöntemi veya alanı `SecuritySafeCritical` `SecurityCritical` `SecurityTransparent` ,,<xref:System.Type.IsSecurityCritical%2A>veya: ,,<xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>ve olduğunu anlamak için, ad alanına aşağıdaki özellikler eklenmiştir. <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> Özniteliğin varlığını denetlemek yerine, yansımayı kullanarak saydamlığı öğrenmek için bu özellikleri kullanın. Saydamlık kuralları karmaşıktır ve öznitelik denetimi yeterli olmayabilir.

> [!NOTE]
> Bir `SafeCritical` yöntemi <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, `true` , `SafeCritical` gerçekten <xref:System.Type.IsSecurityCritical%2A> kritik olduğundan (kritik kodla aynı yeteneklere sahiptir ancak saydam koddan çağrılabilir), her ikisi için de döndürülür.

Dinamik yöntemler, eklendiği modüllerin saydamlığını miras alır; Bunlar, türün saydamlığını (bir türe eklenmişse) almayacaktır.

### <a name="skip-verification-in-full-trust"></a>Tam Güven İçinde Doğrulamayı Atlama

<xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Özelliği<xref:System.Security.SecurityRulesAttribute> özniteliğinde olarak ayarlayarak, tamamen güvenilir saydam derlemeler için doğrulamayı atlayabilirsiniz: `true`

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

Özelliği varsayılan olarak `false` olduğundan, doğrulama atlamak için özelliği olarak `true` ayarlanmalıdır. <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Bu yalnızca iyileştirme amacıyla yapılmalıdır. Derleme içindeki saydam kodun, `transparent` [PEVerify aracında](../tools/peverify-exe-peverify-tool.md)seçeneğini kullanarak doğrulanabilir olduğundan emin olmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliği saydam kod, düzey 1](security-transparent-code-level-1.md)
- [Güvenlik Değişiklikleri](../security/security-changes.md)
