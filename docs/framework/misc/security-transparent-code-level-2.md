---
title: "Güvenliği Saydam Kod, 2. Düzey"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
caps.latest.revision: "37"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba7b6bca4618b8de7c1b5ce2ef45b8455ee71c5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="security-transparent-code-level-2"></a>Güvenliği Saydam Kod, 2. Düzey
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Düzey 2 saydamlık sunulmuştur [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Bu modelin üç tenets şunlardır: saydam kod, güvenlik açısından güvenli-kritik kod ve güvenlik açısından kritik kod.  
  
-   Saydam kod, tam güven çalışan kodu da dahil olmak üzere diğer saydam kod veya yalnızca güvenlik açısından güvenli-kritik kod çağırabilir. Yalnızca, (varsa) etki alanının kısmi güven izni tarafından izin verilen eylemleri de gerçekleştirebilirsiniz. Saydam kod aşağıdakileri yapamazsınız:  
  
    -   Gerçekleştirmek bir <xref:System.Security.CodeAccessPermission.Assert%2A> veya ayrıcalık yükseltme.  
  
    -   Güvenli olmayan veya doğrulanamayan kodu içerir.  
  
    -   Doğrudan kritik kod çağırabilir.  
  
    -   Yerel kod çağrısı veya sahip code <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliği.  
  
    -   Tarafından korunan bir üye çağırın bir <xref:System.Security.Permissions.SecurityAction.LinkDemand>.  
  
    -   Kritik türlerinden devralır.  
  
     Ayrıca, saydam yöntemler kritik sanal yöntemleri geçersiz kılmak veya kritik arabirim yöntemleri uygulayın.  
  
-   Güvenli kritik kodu tam olarak güvenilmeyen ancak saydam kod tarafından çağrılabilir. Tam güven kodunun sınırlı bir yüzey alanını gösterir; doğruluk ve güvenlik Doğrulamalar güvenli kritik kodda gerçekleşir.  
  
-   Güvenlik açısından kritik kod herhangi bir kod çağırabilir ve tam olarak güvenilmeyen ancak tarafından saydam kod çağrılamaz.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Kullanım örnekleri ve davranışları](#examples)  
  
-   [Desenler geçersiz kıl](#override)  
  
-   [Devralma kuralları](#inheritance)  
  
-   [Ek bilgi ve kurallar](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a>Kullanım Örnekleri ve Davranışlar  
 Belirtmek için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] kurallarını (Düzey 2 saydamlık), bir derleme için aşağıdaki ek açıklama kullanın:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 .NET Framework 2.0 kurallara (düzey 1 saydamlık) kilitlemek için aşağıdaki ek açıklama kullanın:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Bir derlemeyi açıklama değil eklerseniz [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] kuralları, varsayılan olarak kullanılır. Ancak, önerilen en iyi uygulama olarak kullanmaktır <xref:System.Security.SecurityRulesAttribute> bağlı olarak varsayılan özniteliği yerine.  
  
### <a name="assembly-wide-annotation"></a>Derleme genelinde ek açıklaması  
 Derleme düzeyindeki öznitelikler kullanımına aşağıdaki kurallar geçerlidir:  
  
-   Hiçbir öznitelik: öznitelik belirtmezseniz, çalışma zamanı tüm kod güvenlik kritik, güvenlik açısından kritik olan bir devralma kuralı burada ihlal dışında olarak yorumlar (örneğin, geçersiz kılma veya saydam bir uygulama, sanal veya arabirim yöntemi ). Bu gibi durumlarda yöntemler güvenli önemlidir. Hiçbir öznitelik belirtilmesi saydamlık kuralları sizin için belirlemek ortak dil çalışma zamanı neden olur.  
  
-   `SecurityTransparent`: Tüm kod saydamdır; Tüm derleme ayrıcalıklı veya güvenli olmayan yapmaz.  
  
-   `SecurityCritical`: Bu derlemedeki türleri tarafından sunulan tüm kod önemlidir; diğer tüm kod saydamdır. Bu senaryoda, tüm öznitelikleri değil belirtme benzer; Ancak, ortak dil çalışma zamanı saydamlık kuralları otomatik olarak belirlemez. Örneğin, bir sanal veya soyut yöntemi geçersiz kılma veya arabirim yöntemi, varsayılan olarak uygulamak, bu yöntem saydamdır. Açıkça yöntemi olarak ek açıklama gerekir `SecurityCritical` veya `SecuritySafeCritical`; Aksi halde, bir <xref:System.TypeLoadException> yükleme zamanında oluşturulur. Bu kural, ayrıca hem temel sınıfını hem de türetilmiş bir sınıf aynı bütünleştirilmiş kodda olduğunda geçerlidir.  
  
-   `AllowPartiallyTrustedCallers`(Düzey 2 yalnızca): tüm varsayılanları saydam kod. Ancak, tek tek türleri ve üyeleri diğer özniteliklere sahip olabilir.  
  
 Aşağıdaki tabloda, Düzey 2 Düzey 1 için derleme düzeyi davranışı karşılaştırır.  
  
|Derleme özniteliği|Düzey 2|Düzey 1|  
|------------------------|-------------|-------------|  
|Kısmen güvenilir bir derleme üzerinde özniteliği yok|Türleri ve üyeleri saydam varsayılan olarak, ancak güvenlik açısından kritik ya da güvenlik açısından güvenli-kritik olabilir.|Tüm türleri ve üyeleri saydamdır.|  
|Bir öznitelik yok|Hiçbir öznitelik belirtilmesi saydamlık kuralları sizin için belirlemek ortak dil çalışma zamanı neden olur. Tüm türleri ve üyeleri güvenlik-burada güvenlik açısından kritik olan bir devralma kuralı ihlal dışında önemlidir.|Tam olarak güvenilir bir derleme üzerinde (genel derleme önbelleğinde veya tam güvende olarak tanımlanan `AppDomain`) tüm türleri saydam ve tüm güvenlik açısından güvenli-kritik üyeleridir.|  
|`SecurityTransparent`|Tüm türleri ve üyeleri saydamdır.|Tüm türleri ve üyeleri saydamdır.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Yok.|Tüm türleri ve üyeleri güvenlik açısından kritik.|  
|`SecurityCritical`|Bu derlemedeki türleri tarafından tanıtılan tüm kod önemlidir; diğer tüm kod saydamdır. Bir sanal veya soyut yöntemi geçersiz kılma veya bir arabirim yöntemini uygulayın, yöntemi olarak açıkça açıklama gerekir `SecurityCritical` veya `SecuritySafeCritical`.|Tüm Varsayılanları saydam kod. Ancak, tek tek türleri ve üyeleri diğer özniteliklere sahip olabilir.|  
  
### <a name="type-and-member-annotation"></a>Tür ve Üye Ek Açıklaması  
 Bir türe uygulanan güvenlik özniteliklerini türü tarafından sunulan üyeleri için de geçerlidir. Ancak, bunlar için sanal uygulamayın veya soyut taban sınıf veya arabirim uygulamaları geçersiz kılar. Tür ve üye düzeyinde öznitelikleri kullanımına aşağıdaki kurallar geçerlidir:  
  
-   `SecurityCritical`: Tür veya üye kritik öneme sahiptir ve yalnızca tam güven kod tarafından çağrılabilir. Güvenlik açısından kritik tür tarafından sunulan yöntemleri önemlidir.  
  
    > [!IMPORTANT]
    >  Temel sınıflar veya arabirimlerini sunulan ve geçersiz veya bir güvenlik açısından kritik sınıfta uygulanan sanal ve soyut yöntemleri, varsayılan olarak görünmez. Bunlar ya da tanımlanmalıdır `SecuritySafeCritical` veya `SecurityCritical`.  
  
-   `SecuritySafeCritical`: Tür veya üye güvenli kritik öneme sahiptir. Ancak, tür veya üye saydam (kısmen güvenilen) koddan çağrılan ve diğer kritik kod özelliğine sahip. Kod için güvenlik denetlenmesi gerekir.  
  
 [Başa dön](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a>Desenleri Geçersiz Kılma  
 Aşağıdaki tabloda, Düzey 2 saydamlık için izin verilen yöntemi geçersiz kılmaları gösterir.  
  
|Temel sanal/arabirim üye|Geçersiz kılma/arabirimi|  
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
  
-   Türler için kuralları: soldan sağa giderek, erişim daha kısıtlayıcı olur. Türetilmiş türler en az temel tür olarak olabildiğince kısıtlayıcı olması gerekir.  
  
-   Kuralları yöntemleri için: türetilmiş yöntemleri temel yöntemden erişilebilirlik değiştiremiyor. İçin varsayılan davranış, değil açıklama eklenen tüm türetilmiş yöntemlerdir `Transparent`. Kritik türleri türevleri geçersiz kılınan yöntemi açıkça olarak açıklama eklenmemiş erişilirse durum için bir özel duruma neden `SecurityCritical`.  
  
 Aşağıdaki tabloda izin verilen türü devralma desenleri gösterilir.  
  
|Taban sınıfı|Türetilmiş sınıf olabilir|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 Aşağıdaki tabloda izin verilmeyen türü devralma desenleri gösterilir.  
  
|Taban sınıfı|Türetilmiş sınıf olamaz|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 Aşağıdaki tabloda izin verilen yöntemi devralma desenleri gösterilir.  
  
|Base yöntemi|Türetilen bir yöntem olabilir|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 Aşağıdaki tabloda izin verilmeyen yöntemi devralma desenleri gösterilir.  
  
|Base yöntemi|Türetilen yöntem olamaz|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  Bu devralma kurallar, Düzey 2 türleri ve üyeleri için geçerlidir. Düzey 1 derlemelerindeki Düzey 2 güvenlik kritik türleri ve üyeleri devralabilirsiniz. Bu nedenle, Düzey 2 türleri ve üyeleri düzey 1 notlar için ayrı devralma taleplerini olması gerekir.  
  
 [Başa dön](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a>Ek Bilgiler ve Kurallar  
  
### <a name="linkdemand-support"></a>LinkDemand Desteği  
 Düzey 2 saydamlık modeli değiştirir <xref:System.Security.Permissions.SecurityAction.LinkDemand> ile <xref:System.Security.SecurityCriticalAttribute> özniteliği. Eski (düzey 1) kodda bir <xref:System.Security.Permissions.SecurityAction.LinkDemand> otomatik olarak işlem görür bir <xref:System.Security.Permissions.SecurityAction.Demand>.  
  
### <a name="reflection"></a>Yansıma  
 (Yalnızca bir özel yöntem veya alan başlattığınız sanki) kritik yönteminin çağrılması veya kritik bir alanın okunması tam güven için talep tetikler. Bu nedenle, kısmi güven kodunun edilemez ise tam güven kod kritik yöntemi çağırabilirsiniz.  
  
 Aşağıdaki özellikler için eklenene <xref:System.Reflection> türü, yöntemi veya alanı olup olmadığını belirlemek için ad alanı `SecurityCritical`, `SecuritySafeCritical`, veya `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, ve <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Öznitelik varlığını denetimi yerine yansıma kullanarak saydamlık belirlemek için bu özellikleri kullanın. Saydamlık kuralları karmaşıktır ve özniteliğini denetimi yeterli olmayabilir.  
  
> [!NOTE]
>  A `SafeCritical` yöntemi döndürür `true` her ikisi için de <xref:System.Type.IsSecurityCritical%2A> ve <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, çünkü `SafeCritical` (kritik kod aynı özelliklerine sahiptir, ancak saydam koddan çağrılabilir) gerçekten önemlidir.  
  
 Dinamik yöntemler bağlı olan modüller saydamlığını devralır; (bir türe bağlıysa) türü saydamlığını devralmaz.  
  
### <a name="skip-verification-in-full-trust"></a>Tam Güven İçinde Doğrulamayı Atlama  
 Ayarlayarak tam güvenilir saydam derlemeler için doğrulama atlayabilirsiniz <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> özelliğine `true` içinde <xref:System.Security.SecurityRulesAttribute> özniteliği:  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Özelliği `false` varsayılan olarak, bu nedenle özelliği ayarlanmalıdır `true` doğrulaması atlanacak. Bu, yalnızca en iyi duruma getirme amacıyla yapılmalıdır. Derlemedeki saydam kod kullanılarak doğrulanabilir olduğundan emin olmanız gerekir `transparent` seçeneğini [PEVerify aracı](../../../docs/framework/tools/peverify-exe-peverify-tool.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenliği saydam kod, düzey 1](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [Güvenlik Değişiklikleri](../../../docs/framework/security/security-changes.md)
