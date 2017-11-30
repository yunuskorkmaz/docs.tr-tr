---
title: "Güvenliği saydam kod, düzey 1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
caps.latest.revision: "32"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bdc1a4f9afb8b1d7cf56b74a329353100accc46d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="security-transparent-code-level-1"></a>Güvenliği saydam kod, düzey 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Saydamlık kısmen güvenilen kod işlevselliği kullanıma daha güvenli .NET Framework kitaplıkları yazma geliştiricilere yardımcı olur. Düzey 1 saydamlık .NET Framework 2.0 sürümünde sunulan ve yalnızca Microsoft içinde öncelikle kullanıldı. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kullanabileceğiniz [Düzey 2 saydamlık](../../../docs/framework/misc/security-transparent-code-level-2.md). Ancak, önceki güvenlik kuralları çalıştırmalısınız eski kod belirleyebilir düzey 1 saydamlık saklanan.  
  
> [!IMPORTANT]
>  Yalnızca uyumluluk düzeyi 1 saydamlığını belirtmeniz gerekir; diğer bir deyişle, kullanan .NET Framework 3.5 veya daha önceki geliştirilen yalnızca kodu için 1 düzeyini belirtmek <xref:System.Security.AllowPartiallyTrustedCallersAttribute> veya saydamlık modelini kullanmıyor. Örneğin, düzey 1 saydamlık kısmen güvenilen arayanlara (APTCA) gelen çağrıları izin .NET Framework 2.0 derlemeler için kullanın. İçin geliştirilen kodu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Düzey 2 saydamlık her zaman kullanın.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Düzey 1 saydamlık modeli](#the_level_1_transparency_model)  
  
-   [Saydamlık öznitelikleri](#transparency_attributes)  
  
-   [Güvenlik saydamlık örnekleri](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a>Düzey 1 saydamlık modeli  
 Düzey 1 saydamlık kullandığınızda, güvenlik saydam, güvenlik açısından güvenli-kritik ve güvenlik açısından kritik yöntemlerin içine kodu ayıran bir güvenlik modeli kullanıyor.  
  
 Tüm bir derleme, bir derlemede bazı sınıflar ya da bir sınıf güvenliği saydam olarak bazı yöntemleri işaretleyebilirsiniz. Güvenliği saydam kod ayrıcalık yükseltme yapamazsınız. Bu kısıtlama üç sonuçları vardır:  
  
-   Güvenliği saydam kod gerçekleştiremez <xref:System.Security.Permissions.SecurityAction.Assert> eylemler.  
  
-   Güvenliği saydam kod tarafından karşılanması herhangi bir bağlantı isteği tam isteğe bağlı olur.  
  
-   Güvenliği saydam kod içinde yürütülmelidir güvenli olmayan (doğrulanamaz) kod için tam talep neden <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> güvenlik izni.  
  
 Bu kurallar, ortak dil çalışma zamanı tarafından (CLR) yürütme sırasında uygulanır. Güvenliği saydam kod geri çağıran kodu tüm güvenlik gereksinimlerini kendi arayanlara geçirir. Güvenliği saydam kod üzerinden akış taleplerini ayrıcalıkları Yükselt olamaz. Düşük güven uygulama güvenliği saydam kod çağırır ve isteğe bağlı yüksek ayrıcalık için neden olursa, isteğe bağlı geri düşük güven kod akış ve başarısız. Güvenliği saydam kod, bu işlemi gerçekleştiremezsiniz için isteğe bağlı durduramıyor Eylemler assert. Başarılı bir talep tam güven kod sonuçlarından aynı güvenliği saydam kod çağrılır.  
  
 Güvenlik açısından kritik güvenlik saydam tersidir. Güvenlik açısından kritik kod tam güven ile yürütür ve tüm ayrıcalıklı işlemler gerçekleştirebilir. Güvenlik açısından güvenli-kritik kod, erişim izni olmadığı kaynakları kullanmak kısmen güvenilen arayanlara izin verme onaylamak için kapsamlı güvenlik denetim boyunca ayrıcalıklı kodudur.  
  
 Saydamlık açıkça uygulamanız gerekmez. Daha az miktarda ayrıcalık yükseltmeleri gerçekleştirir kod güvenlik kritik ya da güvenlik açısından güvenli-kritik olarak işaretlenmiş ancak veri işleme ve mantığı işler kodunuzu çoğunluğu genellikle güvenlik-saydam olarak işaretlenebilir.  
  
> [!IMPORTANT]
>  Düzey 1 saydamlık derleme kapsamına sınırlıdır; derlemeler arasında zorlanmaz. Düzey 1 saydamlık, öncelikle Microsoft bünyesinde güvenlik denetim amacıyla kullanıldı. Diğer derlemelerde güvenliği saydam kod güvenlik kritik türleri ve üyeleri düzey 1 derleme içinde erişebilir. Tam güvende tüm Düzey 1 güvenlik kritik türleri ve üyeleri için bağlantı talepleri gerçekleştirmek önemlidir. Da güvenlik açısından güvenli-kritik türleri ve üyeleri arayanlar tür veya üye tarafından erişilen korumalı kaynaklar için izinlere sahip olduğunuzu doğrulamanız gerekir.  
  
 .NET Framework'ün önceki sürümleriyle geriye dönük uyumluluk için saydamlığı özniteliklerle açıklama değil tüm üyeleri güvenlik açısından güvenli-kritik olduğu kabul edilir. Değil açıklama eklenen tüm türleri saydam olarak kabul edilir. Saydamlık doğrulamak için statik çözümleme kural yok. Bu nedenle, saydamlık hataları çalışma zamanında hata ayıklama gerekebilir.  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a>Saydamlık öznitelikleri  
 Aşağıdaki tabloda kodunuzu saydamlık ek açıklama eklemek için kullandığınız üç öznitelikleri açıklanmaktadır.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Yalnızca derleme düzeyinde izin verilir. Tüm türleri ve derleme güvenliği saydam olarak üyeleri tanımlar. Derleme herhangi bir güvenlik açısından kritik kod içeremez.|  
|<xref:System.Security.SecurityCriticalAttribute>|Derleme düzeyinde olmadan kullanıldığında <xref:System.Security.SecurityCriticalAttribute.Scope%2A> özelliği, varsayılan olarak güvenlik saydam olarak derlemedeki tüm kod tanımlar, ancak derleme güvenlik açısından kritik kod içerebilir gösterir.<br /><br /> Sınıf düzeyinde kullanıldığında, sınıf ya da güvenlik açısından kritik olarak yöntemi, ancak sınıf üyesi değilse tanımlar. Tüm üyeler güvenlik kritik duruma getirmek için ayarlanmış <xref:System.Security.SecurityCriticalAttribute.Scope%2A> özelliğine <xref:System.Security.SecurityCriticalScope.Everything>.<br /><br /> Üye düzeyinde kullanıldığında, öznitelik yalnızca o üyesine uygular.<br /><br /> Sınıf veya üye güvenlik açısından kritik olarak tanımlanan ayrıcalık yükseltmeleri gerçekleştirebilirsiniz. **Önemli:** bunlar gelen derlemenin dışından çağrıldığında düzey 1 saydamlık güvenlik kritik türleri ve üyeleri güvenlik-güvenli-kritik olarak kabul edilir. Güvenlik açısından kritik türleri ve yetkisiz ayrıcalık önlemek için tam güven için bir bağlantı isteği üyeleriyle korumanız gerekir.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Güvenliği saydam kod derlemesi tarafından erişilebilecek güvenlik açısından kritik kod tanımlar. Aksi takdirde, güvenliği saydam kod, özel veya dahili güvenlik açısından kritik üyeleri aynı bütünleştirilmiş kodda erişemiyor. Bunun yapılması, güvenlik açısından kritik kod etkilemek ve ayrıcalık beklenmeyen indirmeyi mümkün kılar. Güvenlik açısından güvenli-kritik kod sıkı güvenlik denetim geçer. **Not:** güvenlik açısından güvenli-kritik türleri ve üyeleri arayanlar çağıran korunan kaynaklara erişim yetkisi olup olmadığını belirlemek için izinleri doğrula gerekir.|  
  
 <xref:System.Security.SecuritySafeCriticalAttribute> Özniteliği güvenliği saydam kod güvenlik kritik üyeleri aynı bütünleştirilmiş kodda erişmek etkinleştirir. Güvenliği saydam ve güvenlik açısından kritik kod derlemenizi içinde iki derlemelerine ayrılmış olarak göz önünde bulundurun. Güvenliği saydam kod güvenlik açısından kritik kod özel veya dahili üyelerini görmek mümkün olmayacaktır. Ayrıca, güvenlik açısından kritik kod erişim ortak arabirimi için genellikle denetlenir. Derleme dışında erişilebilir olması için bir özel veya dahili durumu beklediğiniz değil; Yalıtılmış durumu tutmak isteyebilirsiniz. <xref:System.Security.SecuritySafeCriticalAttribute> Özniteliği durum gerekli olduğunda yalıtım geçersiz kılma olanağı sağlayarak güvenliği saydam ve güvenlik açısından kritik kod arasında yalıtım korur. Güvenliği saydam kod, özel veya dahili güvenlik açısından kritik kod erişemiyor, bu üyeler ile işaretlenmiş sürece <xref:System.Security.SecuritySafeCriticalAttribute>. Uygulamadan önce <xref:System.Security.SecuritySafeCriticalAttribute>, genel olarak açık gibi bu üye denetleme.  
  
### <a name="assembly-wide-annotation"></a>Derleme genelinde ek açıklaması  
 Aşağıdaki tabloda derleme düzeyinde güvenlik öznitelikleri kullanmanın etkileri açıklanmaktadır.  
  
|Derleme özniteliği|Derleme durumu|  
|------------------------|--------------------|  
|Kısmen güvenilir bir derleme üzerinde özniteliği yok|Tüm türleri ve üyeleri saydamdır.|  
|Tam olarak güvenilir bir derleme hiçbir özniteliği (genel derleme önbelleğinde veya tam güvende olarak tanımlanan `AppDomain`)|Tüm türleri saydam ve tüm üyelerin güvenlik açısından güvenli-kritik durumda.|  
|`SecurityTransparent`|Tüm türleri ve üyeleri saydamdır.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Tüm türleri ve üyeleri güvenlik açısından kritik.|  
|`SecurityCritical`|Tüm Varsayılanları saydam kod. Ancak, tek tek türleri ve üyeleri diğer özniteliklere sahip olabilir.|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a>Güvenlik saydamlık örnekleri  
 .NET Framework 2.0 saydamlık kuralları (düzey 1 saydamlık) kullanmak için aşağıdaki derleme ek açıklama kullanın:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Tam bir derleme derleme herhangi bir kritik kod içermiyor ve herhangi bir şekilde ayrıcalık yükseltmesine değil belirtmek için saydam hale getirmek istiyorsanız, aşağıdaki öznitelik derleme saydamlık açıkça ekleyebilirsiniz:  
  
```  
[assembly: SecurityTransparent]  
```  
  
 Kritik ve saydam aynı bütünleştirilmiş kodda karıştırmak istiyorsanız, derleme işaretleyerek Başlat <xref:System.Security.SecurityCriticalAttribute> özniteliğini derleme kritik kod şu şekilde içerebilir belirtmek için:  
  
```  
[assembly: SecurityCritical]  
```  
  
 Güvenlik açısından kritik eylemleri gerçekleştirmek istiyorsanız, başka bir kritik eylem gerçekleştirecek kod açıkça işaretlemelisiniz <xref:System.Security.SecurityCriticalAttribute> aşağıdaki kod örneğinde gösterildiği gibi öznitelik:  
  
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
  
 Önceki kod dışında saydamdır `Critical` açıkça gibi güvenlik açısından kritik olarak işaretlenmiş yöntemi. Saydamlık bile derleme düzeyi ile varsayılan ayar olan <xref:System.Security.SecurityCriticalAttribute> özniteliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenliği saydam kod, Düzey 2](../../../docs/framework/misc/security-transparent-code-level-2.md)  
 [Güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md)
