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
ms.openlocfilehash: 62c25b14fa7b3867bbdbcb2f1e08cc16ce349e72
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156084"
---
# <a name="security-transparent-code-level-2"></a>Güvenliği Saydam Kod, 2. Düzey
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Düzey 2 saydamlık öğesinde tanıtılmıştır [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Bu modelin üç İlkesi saydam kod güvenlik güvenli kritik kod ve güvenlik açısından kritik kod ' dir.  
  
-   Saydam kod tam güven çalışan kodu da dahil olmak üzere, diğer saydam kod veya yalnızca güvenlik-güvenli-kritik kodu çağırabilir. Yalnızca, (varsa) ayarlayın etki alanının kısmi güven izni tarafından izin verilen eylemleri de gerçekleştirebilir. Saydam kod aşağıdaki işlemleri yapamaz:  
  
    -   Gerçekleştirmek bir <xref:System.Security.CodeAccessPermission.Assert%2A> veya ayrıcalık yükseltme.  
  
    -   Güvenli olmayan veya doğrulanamaz kod içerir.  
  
    -   Doğrudan kritik kodu çağırın.  
  
    -   Yerel koda çağrı yapma veya kod <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliği.  
  
    -   Tarafından korunan üyeyi çağırın bir <xref:System.Security.Permissions.SecurityAction.LinkDemand>.  
  
    -   Kritik türlerden devral  
  
     Ayrıca, saydam yöntemleri kritik sanal yöntemleri geçersiz kılmaz veya kritik arabirim yöntemlerini uygulamaz.  
  
-   Güvenli kritik kod, tam olarak güvenilirdir ancak saydam kod tarafından çağrılabilir. Bu, tam güven kodu sınırlı yüzey alanı sunar; düzeltmeler ve güvenlik doğrulamaları güvenli kritik kodda olur.  
  
-   Güvenlik açısından kritik kod, herhangi bir kodu çağırabilir ve tam olarak güvenilirdir ancak saydam kod tarafından çağrılamaz.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Kullanım örnekleri ve davranışlar](#examples)  
  
-   [Desenleri geçersiz kılma](#override)  
  
-   [Devralma kuralları](#inheritance)  
  
-   [Ek bilgiler ve kurallar](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a>Kullanım Örnekleri ve Davranışlar  
 Belirtmek için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] (Düzey 2 saydamlık) kuralları, bir derleme için aşağıdaki ek açıklama kullanın:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 .NET Framework 2.0 kuralları (düzey 1 saydamlık) kilitlemek için aşağıdaki ek açıklama kullanın:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Bir derlemeyi not ekleyemezsiniz, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] kuralları, varsayılan olarak kullanılır. Ancak, önerilen en iyi kullanmaktır <xref:System.Security.SecurityRulesAttribute> bağlı olarak varsayılan öznitelik yerine.  
  
### <a name="assembly-wide-annotation"></a>Derleme genelinde ek açıklaması  
 Öznitelikleri derleme düzeyinde kullanımı için aşağıdaki kurallar geçerlidir:  
  
-   Hiçbir öznitelik: Herhangi bir özniteliği belirtmezseniz, çalışma zamanı, tüm kod güvenlik kritik, burada güvenlik açısından kritik olan bir devralma kuralı ihlal dışında olarak yorumlar. (örneğin, geçersiz kılma veya saydam bir uygulama sanal ya da arabirim yöntemi). Bu gibi durumlarda, güvenli kritik yöntemlerdir. Hiçbir öznitelik belirtmemeye sizin için saydamlık kuralları belirlemek ortak dil çalışma zamanı neden olur.  
  
-   `SecurityTransparent`: Tüm kod saydamdır; Tüm derleme ayrıcalıklı veya güvenli olmayan hiçbir şey yapmaz.  
  
-   `SecurityCritical`: Bu derlemedeki türleri tarafından tanıtılan tüm kod büyük/küçük harf önemlidir; diğer tüm kod saydamdır. Bu senaryo, herhangi bir özniteliği değil belirtme benzer. Ancak, ortak dil çalışma zamanı, saydamlık kuralları otomatik olarak belirlemez. Örneğin, bu yöntem sanal veya soyut bir yöntemi geçersiz kılın veya varsayılan bir arabirim yöntemini uygulamak, saydamdır. Açıkça yöntemi olarak ek açıklama gerekir `SecurityCritical` veya `SecuritySafeCritical`; Aksi takdirde bir <xref:System.TypeLoadException> yükleme zamanında oluşturulur. Bu kural, ayrıca temel sınıfını hem türetilen sınıfın aynı bütünleştirilmiş kodda olduğunda geçerlidir.  
  
-   `AllowPartiallyTrustedCallers` (Düzey 2 yalnızca): Tüm Varsayılanları saydam kod. Ancak, tek tek türleri ve üyeleri diğer özniteliklere sahip olabilir.  
  
 Aşağıdaki tabloda, düzey 1 Düzey 2 için derleme düzeyi davranışı karşılaştırır.  
  
|Bütünleştirilmiş kod özniteliği|Düzey 2|Düzey 1|  
|------------------------|-------------|-------------|  
|Kısmen güvenilen bir derleme üzerinde herhangi bir öznitelik yok|Türleri ve üyeleri varsayılan olarak saydam olan, ancak güvenlik açısından kritik veya güvenlik güvenli kritik olabilir.|Tüm türler ve üyeler görünmez.|  
|Bir öznitelik yok|Hiçbir öznitelik belirtmemeye sizin için saydamlık kuralları belirlemek ortak dil çalışma zamanı neden olur. Tüm türleri ve üyeleri güvenlik-burada güvenlik açısından kritik olan bir devralma kuralı ihlal ediyor dışında önemlidir.|Tam olarak güvenilen bir derleme üzerinde (genel derleme önbelleğinde veya tam güven olarak tanımlanan `AppDomain`) tüm türleri şeffaftır ve tüm üyeleri güvenlik-güvenli-kritik.|  
|`SecurityTransparent`|Tüm türler ve üyeler görünmez.|Tüm türler ve üyeler görünmez.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Geçerli değildir.|Tüm türleri ve üyeleri güvenlik kritik öneme sahiptir.|  
|`SecurityCritical`|Bu derlemedeki türleri tarafından tanıtılan tüm kod büyük/küçük harf önemlidir; diğer tüm kod saydamdır. Sanal veya soyut bir yöntemi geçersiz kılmak veya bir arabirimin yöntemini uygulayan yöntemi olarak açıkça açıklama gerekir `SecurityCritical` veya `SecuritySafeCritical`.|Tüm Varsayılanları saydam kod. Ancak, tek tek türleri ve üyeleri diğer özniteliklere sahip olabilir.|  
  
### <a name="type-and-member-annotation"></a>Tür ve Üye Ek Açıklaması  
 Bir türe uygulanan güvenlik öznitelikleri türü tarafından sunulan üyeler için de geçerlidir. Ancak, bunlar için sanal uygulanmaz veya soyut temel sınıf veya arabirim uygulamaları geçersiz kılar. Tür ve üye düzeyinde öznitelikler kullanımı için aşağıdaki kurallar geçerlidir:  
  
-   `SecurityCritical`: Türe veya üyeye kritik öneme sahiptir ve yalnızca tam güvenilir kod tarafından çağrılabilir. Güvenlik açısından kritik bir tür içinde sunulan yöntemleri kritik öneme sahiptir.  
  
    > [!IMPORTANT]
    >  Temel sınıflar ya da arabirimleri, dahil edilen ve geçersiz kılınmış veya uygulanan güvenlik açısından kritik bir sınıfta sanal ve Özet yöntemleri tarafından varsayılan olarak görünmez. Bunlar olarak tanımlanmalıdır `SecuritySafeCritical` veya `SecurityCritical`.  
  
-   `SecuritySafeCritical`: Türe veya üyeye güvenli kritik öneme sahiptir. Ancak, türe veya üyeye (kısmen güvenilen) saydam koddan çağrılabilir ve diğer kritik kod özelliğine sahip. Kod için güvenlik denetlenmesi gerekir.  
  
 [Başa dön](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a>Desenleri Geçersiz Kılma  
 Aşağıdaki tabloda, Düzey 2 saydamlık için izin verilen yöntemi geçersiz kılmaları gösterir.  
  
|Temel sanal/arabirim üyesi|Geçersiz kılma/arabirimi|  
|------------------------------------|-------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [Başa dön](#top)  
  
<a name="inheritance"></a>   
## <a name="inheritance-rules"></a>Devralma Kuralları  
 Bu bölümde, aşağıdaki sırayla atanan `Transparent`, `Critical`, ve `SafeCritical` kod tabanlı erişim ve özellikleri:  
  
 `Transparent` < `SafeCritical` < `Critical`  
  
-   Kural türü için: Soldan sağa doğru giden, erişim daha kısıtlayıcı haline gelir. Türetilen türlerin, en az bir temel tür olarak olabildiğince kısıtlayıcı olmalıdır.  
  
-   Kuralları yöntemleri için: Türetilmiş yöntemleri erişilebilirlik taban yöntemden değiştiremezsiniz. Varsayılan davranışı için değil açıklamalı olan tüm türetilmiş yöntemlerdir `Transparent`. Kritik türler CIM'in neden bir özel geçersiz kılınan yöntemi açıkça olarak değil eklenmişse durum `SecurityCritical`.  
  
 Aşağıdaki tabloda, izin verilen tür devralma desenleri gösterir.  
  
|Temel sınıf|Türetilmiş sınıf olabilir|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 Aşağıdaki tabloda, izin verilmeyen türü devralma desenleri gösterir.  
  
|Temel sınıf|Türetilmiş sınıf olamaz|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 Aşağıdaki tabloda, izin verilen yöntemi devralma desenleri gösterir.  
  
|Taban yöntemi|Türetilen bir yöntem olabilir|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 Aşağıdaki tabloda, izin verilmeyen yöntemi devralma desenleri gösterir.  
  
|Taban yöntemi|Türetilmiş yöntemi olamaz|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  Bu devralma kuralları, Düzey 2 türler ve üyeler için geçerlidir. Düzey 1 bütünleştirilmiş kodlar içindeki türleri, Düzey 2 güvenlik kritik türleri ve üyeleri devralabilir. Bu nedenle, Düzey 2 türler ve üyeler için düzey 1 devralanlar ayrı devralma taleplerini olması gerekir.  
  
 [Başa dön](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a>Ek Bilgiler ve Kurallar  
  
### <a name="linkdemand-support"></a>LinkDemand Desteği  
 Düzey 2 saydamlık modelinin yerini <xref:System.Security.Permissions.SecurityAction.LinkDemand> ile <xref:System.Security.SecurityCriticalAttribute> özniteliği. Eski (düzey 1) kodda, bir <xref:System.Security.Permissions.SecurityAction.LinkDemand> otomatik olarak kabul edilir bir <xref:System.Security.Permissions.SecurityAction.Demand>.  
  
### <a name="reflection"></a>Yansıma  
 (Yalnızca özel metodu nebo pole başlattığınız yokmuş gibi) isteğe bağlı tam güven için kritik bir yöntem çağırma veya bir kritik alanının okunmasını tetikler. Bu nedenle, kısmi güven kodu olamaz ancak tam güven kodu kritik bir yöntem çağırabilirsiniz.  
  
 Aşağıdaki özellikler eklenmiştir <xref:System.Reflection> türü, yöntemi veya alan olup olmadığını belirlemek için ad alanı `SecurityCritical`, `SecuritySafeCritical`, veya `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, ve <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Öznitelik varlığını denetleme yerine yansıma kullanarak saydamlığı belirlemek için bu özellikleri kullanın. Saydamlık kuralları karmaşıktır ve denetimi özniteliği için yeterli olmayabilir.  
  
> [!NOTE]
>  A `SafeCritical` yöntemi döndürür `true` hem <xref:System.Type.IsSecurityCritical%2A> ve <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, çünkü `SafeCritical` (kritik kod ile aynı özellikleri vardır, ancak saydam koddan çağrılabilir) gerçekten de önemlidir.  
  
 Dinamik yöntemler için eklenen modülleri saydamlığını devralır; (bir türe ekliyse) türü saydamlığını devralmaz.  
  
### <a name="skip-verification-in-full-trust"></a>Tam Güven İçinde Doğrulamayı Atlama  
 Doğrulama için saydam tamamen güvenilir derlemelerinin ayarlayarak atlayabilirsiniz <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> özelliğini `true` içinde <xref:System.Security.SecurityRulesAttribute> özniteliği:  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Özelliği `false` varsayılan olarak, bu nedenle özelliği ayarlanmalıdır `true` doğrulamayı atlamasına. Bu, yalnızca en iyi duruma getirme amacıyla yapılmalıdır. Saydam kod derleme içindeki kullanılarak doğrulanabilir olduğundan emin olmanız gerekir `transparent` seçeneğini [PEVerify aracı](../../../docs/framework/tools/peverify-exe-peverify-tool.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliği saydam kod, düzey 1](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [Güvenlik Değişiklikleri](../../../docs/framework/security/security-changes.md)
