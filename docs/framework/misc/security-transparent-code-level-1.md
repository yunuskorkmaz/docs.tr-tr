---
title: Güvenliği saydam kod, düzey 1
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afec37a6510e445f1fe2c430684099af967be0ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59161076"
---
# <a name="security-transparent-code-level-1"></a>Güvenliği saydam kod, düzey 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Saydamlık, kısmen güvenilen kod işlevselliği kullanıma sunan daha güvenli .NET Framework kitaplıkları yazma geliştiricilerin yardımcı olur. Düzey 1 saydamlık, .NET Framework 2.0 sürümünde kullanıma sunulmuştur ve yalnızca Microsoft'ta öncelikli olarak kullanıldı. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kullanabileceğiniz [Düzey 2 saydamlık](../../../docs/framework/misc/security-transparent-code-level-2.md). Ancak, eski güvenlik kuralları çalıştırmalısınız eski kodu bulabilmeniz düzey 1 saydamlık korundu.  
  
> [!IMPORTANT]
>  Yalnızca uyumluluk için düzey 1 saydamlığını belirtmelisiniz; diğer bir deyişle, kullandığı .NET Framework 3.5 veya daha önce geliştirilmiştir yalnızca kod için düzey 1 belirtin <xref:System.Security.AllowPartiallyTrustedCallersAttribute> veya saydamlık modeli kullanmayan. Örneğin, kısmen güvenilmeyen çağrıcılara (APTCA) gelen çağrıları izin veren .NET Framework 2.0 derlemeleri için seviye 1 saydamlık kullanın. İçin geliştirilmiş kod için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], her zaman Düzey 2 Asetatını kullanın.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Düzey 1 saydamlık modeli](#the_level_1_transparency_model)  
  
-   [Saydamlık öznitelikleri](#transparency_attributes)  
  
-   [Güvenlik saydamlık örnekleri](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a>Düzey 1 saydamlık modeli  
 Düzey 1 saydamlık kullandığınızda, güvenlik açısından saydam güvenlik-güvenli-kritik ve kritik güvenlik yöntemleri koddan ayıran bir güvenlik modeli kullandığınız.  
  
 Tüm derleme, bir derlemede bazı sınıflar veya bazı yöntemler bir sınıftaki güvenlik açısından saydam olarak işaretleyebilirsiniz. Güvenliği saydam kod ayrıcalıklarını yükseltme yapamazsınız. Bu kısıtlama, üç sonuçları vardır:  
  
-   Güvenliği saydam kod gerçekleştiremezsiniz <xref:System.Security.Permissions.SecurityAction.Assert> eylemler.  
  
-   Güvenliği saydam kod tarafından karşılanması herhangi bir bağlantı talebi tam isteğe bağlı olur.  
  
-   Güvenliği saydam kod yürütülmesi gereken tüm güvenli olmayan (doğrulanamayan) kodu için talepte bulunur neden <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> güvenlik izni.  
  
 Bu kurallar, ortak dil çalışma zamanı tarafından (CLR) yürütme sırasında uygulanır. Güvenliği saydam kod için çağrıda bulunanların geri çağıran kod, tüm güvenlik gereksinimlerini geçirir. Güvenliği saydam kod akış taleplerini ayrıcalıklarını yükseltme yapamazsınız. Düşük güven uygulama güvenliği saydam kod çağırır ve talep etmek için yüksek ayrıcalık neden olur, isteğe bağlı Akış düşük güven kodu ve başarısız olur. Güvenliği saydam kod, gerçekleştirilemiyor çünkü talep durdurulamıyor eylemleri onay. Aynı güvenliği saydam kod tam güven kodu sonuçlarında başarılı bir istek çağrılır.  
  
 Güvenlik açısından kritik güvenliği saydam tersidir. Güvenlik açısından kritik kod tam güven ile yürütülür ve tüm ayrıcalıklı işlemleri gerçekleştirebilir. Güvenlik-güvenli-kritik kodu erişim iznine sahip değil kaynakları kullanmak, kısmen güvenilmeyen çağrıcılara izin vermeyecek onaylamak için kapsamlı güvenlik denetim alınıp ayrıcalıklı kodudur.  
  
 Saydamlık açıkça uygulamanız gerekmez. Daha kısa bir ayrıcalık yükseltmeleri gerçekleştiren kod güvenlik kritik veya güvenlik güvenli kritik olarak işaretlenmiş ancak veri işleme ve mantığı işler kodunuzu çoğunu genellikle güvenlik açısından saydam olarak, işaretlenebilir.  
  
> [!IMPORTANT]
>  Düzey 1 saydamlık, derlemenin kapsamını sınırlıdır; derlemeler arasında zorlanmaz. Düzey 1 saydamlık, güvenlik denetimi amacıyla Microsoft'ta öncelikli olarak kullanıldı. Kritik güvenlik türleri ve üyeleri bir düzey 1 derleme içinde diğer derlemelerdeki güvenlik saydam kodu tarafından erişilebilir. Tüm düzey 1 kritik güvenlik türleri ve üyeleri tam güven için bağlantı isteklerini gerçekleştirmek önemlidir. Ayrıca güvenlik-güvenli-kritik türler ve üyeler çağıranlar tür veya üye tarafından erişilen korumalı kaynaklara için izinlere sahip olduğunuzu onaylamanız gerekir.  
  
 .NET Framework'ün önceki sürümleriyle geriye dönük uyumluluk için saydamlık özniteliklerle ek açıklama değil tüm üyeleri güvenlik-güvenli-kritik olarak değerlendirilir. Açıklamalı olmayan tüm türleri saydam olarak kabul edilir. Saydamlık doğrulamak için statik çözümleme kural yok. Bu nedenle, saydamlık hataları çalışma zamanında hata ayıklama gerekebilir.  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a>Saydamlık öznitelikleri  
 Aşağıdaki tabloda, kodunuz için saydamlık ek açıklama eklemek için kullandığınız üç öznitelikleri açıklar.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Yalnızca derleme düzeyinde izin verilir. Tüm türleri ve üyeleri güvenlik açısından saydam olarak derlemeyi tanımlar. Derleme, güvenlik açısından kritik kod içeremez.|  
|<xref:System.Security.SecurityCriticalAttribute>|Derleme düzeyinde olmadan kullanıldığında <xref:System.Security.SecurityCriticalAttribute.Scope%2A> özelliği varsayılan olarak güvenlik açısından saydam olarak derlemedeki tüm kodlar tanımlar, ancak derleme güvenlik açısından kritik kod içerebilir gösterir.<br /><br /> Sınıf düzeyinde kullanıldığında, sınıf veya yöntemi olarak güvenlik açısından kritik, ancak sınıfın üyelerini tanımlar. Tüm üyelere güvenlik açısından kritik hale getirmek için ayarlanmış <xref:System.Security.SecurityCriticalAttribute.Scope%2A> özelliğini <xref:System.Security.SecurityCriticalScope.Everything>.<br /><br /> Üye düzeyinde kullanıldığında, özniteliği yalnızca bu üye için geçerlidir.<br /><br /> Sınıf veya üye güvenlik açısından kritik olarak tanımlanan ayrıcalık yükseltmeleri gerçekleştirebilirsiniz. **Önemli:**  Bunlar gelen derlemenin dışından çağrıldığında düzey 1 saydamlık, güvenlik açısından kritik türleri ve üyeleri güvenlik-güvenli-kritik olarak kabul edilir. Kritik güvenlik türleri ve yetkisiz ayrıcalık önlemek için tam güven için bağlantı talebi üyeleriyle korumanız gerekir.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Derleme güvenliği saydam kod tarafından erişilebilen güvenlik açısından kritik kod tanımlar. Aksi takdirde, güvenliği saydam kod, özel veya iç güvenlik açısından kritik üyeleri aynı bütünleştirilmiş kodun erişemez. Bunun yapılması, güvenlik açısından kritik kod etkilemek ve ayrıcalık beklenmeyen indirmeyi mümkün kılar. Güvenlik güvenli kritik kod, katı güvenlik denetim geçmelidir. **Not:**  Güvenlik-güvenli-kritik türler ve üyeler çağıran korunan kaynaklara erişim yetkisi olup olmadığını belirlemek için çağıranlar izinlerini doğrulamanız gerekir.|  
  
 <xref:System.Security.SecuritySafeCriticalAttribute> Özniteliği aynı derleme içinde güvenlik açısından kritik üyelere erişim güvenlik saydam kodu sağlar. Derlemenizi güvenlik açısından saydam ve güvenlik açısından kritik kodda iki derlemelerine ayrılmış olarak göz önünde bulundurun. Güvenliği saydam kod güvenlik açısından kritik kod özel veya iç üyelerini görmeniz mümkün olmayacaktır. Ayrıca, güvenlik açısından kritik kod, genellikle erişim için ortak arabirimi denetlenir. Bir özel veya iç durumu derlemenin dışından erişilebilir olmasını beklediğiniz değil; Yalıtılmış durumu tutmak istersiniz. <xref:System.Security.SecuritySafeCriticalAttribute> Öznitelik durumu gerekli olduğunda yalıtım geçersiz kılma olanağı sağlarken, güvenlik açısından saydam ve güvenlik açısından kritik kod arasında yalıtım tutar. Güvenliği saydam kod, özel veya iç güvenlik açısından kritik kod erişemez, bu üyeler ile işaretlenmiş sürece <xref:System.Security.SecuritySafeCriticalAttribute>. Uygulamadan önce <xref:System.Security.SecuritySafeCriticalAttribute>, genel olarak ifşa edildi gibi bu üyenin denetim.  
  
### <a name="assembly-wide-annotation"></a>Derleme genelinde ek açıklaması  
 Aşağıdaki tabloda derleme düzeyinde güvenlik özniteliklerini kullanmanın etkileri açıklanmaktadır.  
  
|Bütünleştirilmiş kod özniteliği|Derleme durumu|  
|------------------------|--------------------|  
|Kısmen güvenilen bir derleme üzerinde herhangi bir öznitelik yok|Tüm türler ve üyeler görünmez.|  
|Tam olarak güvenilen bir derleme üzerinde hiçbir öznitelik (genel derleme önbelleğinde veya tam güven olarak tanımlanan `AppDomain`)|Tüm türleri saydam ve tüm üyeleri güvenlik-güvenli-kritik.|  
|`SecurityTransparent`|Tüm türler ve üyeler görünmez.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Tüm türleri ve üyeleri güvenlik kritik öneme sahiptir.|  
|`SecurityCritical`|Tüm Varsayılanları saydam kod. Ancak, tek tek türleri ve üyeleri diğer özniteliklere sahip olabilir.|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a>Güvenlik saydamlık örnekleri  
 .NET Framework 2.0 saydamlık kuralları (düzey 1 saydamlık) kullanmak için aşağıdaki derleme ek açıklama kullanın:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Tüm derleme derleme herhangi bir kritik kod içermiyor ve herhangi bir şekilde ayrıcalıklarını yükseltme değil belirtmek için saydam hale getirmek isterseniz, saydamlık derleme şu özniteliği ile açıkça ekleyebilirsiniz:  
  
```  
[assembly: SecurityTransparent]  
```  
  
 Kritik ve saydam kodu aynı bütünleştirilmiş kodun karışımı istiyorsanız, derleme ile işaretleyerek başlayın <xref:System.Security.SecurityCriticalAttribute> derleme gibi kritik kod içerebilir belirtmek için özniteliği:  
  
```  
[assembly: SecurityCritical]  
```  
  
 Güvenlik açısından kritik eylemleri gerçekleştirmek istiyorsanız, başka bir kritik eylemi gerçekleştiren kod açıkça işaretlemelisiniz <xref:System.Security.SecurityCriticalAttribute> aşağıdaki kod örneğinde gösterildiği gibi öznitelik:  
  
```  
[assembly: SecurityCritical]  
Public class A  
{  
    [SecurityCritical]  
    private void Critical()  
    {  
        // critical  
    }  
  
    public int SomeProperty  
    {  
        get {/* transparent */ }  
        set {/* transparent */ }  
    }  
}  
public class B  
{      
    internal string SomeOtherProperty  
    {  
        get { /* transparent */ }  
        set { /* transparent */ }  
    }  
}  
```  
  
 Önceki kodun dışında saydamdır `Critical` açıkça gibi güvenlik açısından kritik olarak işaretlenmiş yöntemi. Saydamlık bile, derleme düzeyi ile varsayılan ayar olan <xref:System.Security.SecurityCriticalAttribute> özniteliği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliği saydam kod, Düzey 2](../../../docs/framework/misc/security-transparent-code-level-2.md)
- [Güvenlik Değişiklikleri](../../../docs/framework/security/security-changes.md)
