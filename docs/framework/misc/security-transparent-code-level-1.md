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
ms.openlocfilehash: 8f232a7724ad831818627cbfc2845ea808a3fcfd
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215802"
---
# <a name="security-transparent-code-level-1"></a>Güvenliği saydam kod, düzey 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Saydamlık, geliştiricilerin kısmen güvenilen koda işlevsellik sunan daha güvenli .NET Framework kitaplıklar yazmasını sağlar. 1\. düzey saydamlık .NET Framework sürüm 2,0 ' de tanıtılmıştı ve öncelikle yalnızca Microsoft içinde kullanılmıştı. 4\. .NET Framework başlayarak [düzey 2 saydamlığını](security-transparent-code-level-2.md)kullanabilirsiniz. Ancak, 1. düzey saydamlık, önceki güvenlik kuralları ile çalışması gereken eski kodu tanımlayabilmeniz için korunur.  
  
> [!IMPORTANT]
> Düzey 1 saydamlığı yalnızca uyumluluk için belirtmelisiniz; diğer bir deyişle, yalnızca <xref:System.Security.AllowPartiallyTrustedCallersAttribute> kullanan veya saydamlık modelini kullanmayan .NET Framework 3,5 veya önceki bir sürümüyle geliştirilmiş kod için düzey 1 ' i belirtin. Örneğin, kısmen güvenilen çağıranların (APTCA) çağrılara izin veren .NET Framework 2,0 derlemeleri için düzey 1 saydamlığı kullanın. .NET Framework 4 için geliştirilen kod için her zaman düzey 2 saydamlığı kullanın.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Düzey 1 saydamlık modeli](#the_level_1_transparency_model)  
  
- [Saydamlık öznitelikleri](#transparency_attributes)  
  
- [Güvenlik saydamlığı örnekleri](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a>Düzey 1 saydamlık modeli  
 Düzey 1 saydamlık kullandığınızda, kodu güvenlik açısından saydam, güvenlik açısından güvenli-kritik ve güvenlik açısından kritik yöntemlere ayıran bir güvenlik modeli kullanıyorsunuz.  
  
 Tüm bir derlemeyi, bir derlemedeki bazı sınıfları veya bir sınıftaki bazı yöntemleri güvenlik açısından saydam olarak işaretleyebilirsiniz. Güvenliği saydam kod ayrıcalıkları yükseltemez. Bu kısıtlama üç sonuçlara sahiptir:  
  
- Güvenliği saydam kod <xref:System.Security.Permissions.SecurityAction.Assert> eylemleri gerçekleştiremez.  
  
- Güvenliği saydam kod tarafından karşılanması gereken herhangi bir bağlantı talebi, tam talep haline gelir.  
  
- Güvenlik açısından saydam kodda yürütülmesi gereken güvenli olmayan (doğrulanamayan) kod, <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> güvenlik izni için tam talebe neden olur.  
  
 Bu kurallar, ortak dil çalışma zamanı (CLR) tarafından yürütme sırasında zorlanır. Güvenliği saydam kod, geri arayanlara geri çağrı yaptığı kodun tüm güvenlik gereksinimlerini geçirir. Güvenlik açısından saydam kod üzerinden akan talepler ayrıcalıkların yükselmez. Düşük öncelikli bir uygulama, güvenlik açısından saydam kodu çağırırsa ve yüksek ayrıcalıklı bir talebe neden oluyorsa, talep düşük güven koduna geri akacaktır ve başarısız olur. Güvenlik saydam kodu, onay eylemleri gerçekleştiremediğinden isteği durduramıyor. Tam güven kodundan çağrılan aynı güvenlik saydam kodu, başarılı bir talebe neden olur.  
  
 Güvenlik açısından kritik, güvenlik açısından şeffaf bir tersidir. Güvenlik açısından kritik kod tam güvenle yürütülür ve tüm ayrıcalıklı işlemleri gerçekleştirebilir. Güvenli kritik kod, kısmen güvenilen çağıranların erişim izni olmayan kaynakları kullanmasına izin vermediğini onaylamak için kapsamlı bir güvenlik denetimi aracılığıyla oluşturulmuş ayrıcalıklı koddur.  
  
 Saydamlığı açıkça uygulamanız gerekir. Veri işleme ve mantığını işleyen kodunuzun büyük bölümü genellikle güvenlik açısından saydam olarak işaretlenebilir, ancak ayrıcalıkların yükseltme işlemini gerçekleştiren daha az miktarda kod miktarı güvenlik açısından kritik veya güvenlik açısından güvenli olarak işaretlenir.  
  
> [!IMPORTANT]
> Düzey 1 saydamlık, derleme kapsamıyla sınırlıdır; derlemeler arasında zorlanmaz. Düzey 1 saydamlık öncelikle Microsoft 'un güvenlik denetimi amacıyla kullanıldığı bir şekilde kullanılır. Düzey 1 derlemesi içindeki güvenlik açısından kritik türlere ve üyelere, diğer derlemelerde güvenlik açısından saydam kod tarafından erişilebilir. Tüm düzey 1 güvenlik açısından kritik türlerde ve üyelerde tam güven için bağlantı talepleri gerçekleştirmeniz önemlidir. Güvenlik açısından kritik olan türler ve Üyeler, çağıranların tür veya üye tarafından erişilen korunan kaynaklar için izinlere sahip olduğunu da doğrulamamalıdır.  
  
 .NET Framework önceki sürümleriyle geriye dönük uyumluluk için, saydamlık öznitelikleriyle açıklama eklenmiş olmayan tüm Üyeler güvenlik açısından kritik olarak kabul edilir. Açıklamalı olmayan tüm türler saydam olarak değerlendirilir. Saydamlığı doğrulamaya yönelik bir statik analiz kuralı yok. Bu nedenle, çalışma zamanında saydam hatalarda hata ayıklaması yapmanız gerekebilir.  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a>Saydamlık öznitelikleri  
 Aşağıdaki tabloda, saydamlığa yönelik kodunuza açıklama eklemek için kullandığınız üç öznitelik açıklanmaktadır.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Yalnızca derleme düzeyinde izin verilir. Derlemedeki tüm türleri ve üyeleri güvenlik açısından saydam olarak tanımlar. Derleme, güvenlik açısından kritik kod içeremez.|  
|<xref:System.Security.SecurityCriticalAttribute>|Derleme düzeyinde <xref:System.Security.SecurityCriticalAttribute.Scope%2A> özelliği olmadan kullanıldığında, derlemedeki tüm kodu varsayılan olarak güvenlik açısından saydam olarak tanımlar, ancak derlemenin güvenlik açısından kritik kod içerebileceğini gösterir.<br /><br /> Sınıf düzeyinde kullanıldığında, sınıfı veya yöntemi, sınıfın üyelerini değil, güvenlik açısından kritik olarak tanımlar. Tüm üyelerin güvenlik açısından kritik olmasını sağlamak için <xref:System.Security.SecurityCriticalAttribute.Scope%2A> özelliğini <xref:System.Security.SecurityCriticalScope.Everything>olarak ayarlayın.<br /><br /> Üye düzeyinde kullanıldığında, özniteliği yalnızca o üye için geçerlidir.<br /><br /> Güvenlik açısından kritik olarak tanımlanan sınıf veya üye, ayrıcalık yükseltme işlemini gerçekleştirebilir. **Önemli:**  Düzey 1 saydamlıkla, güvenlik açısından kritik türler ve Üyeler, derleme dışından çağrıldığında güvenlik açısından kritik öneme sahip olarak değerlendirilir. Ayrıcalık yükselmesine engel olmak için, güvenlik açısından kritik türleri ve üyeleri tam güven için bir bağlantı talebi ile korumanız gerekir.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Derlemede güvenlik açısından saydam kod tarafından erişilebilen güvenlik açısından kritik kodu belirler. Aksi takdirde, güvenlik açısından saydam kod aynı derlemede özel veya iç güvenlik açısından kritik üyelere erişemez. Bunun yapılması, güvenlik açısından kritik kodu etkiler ve olası ayrıcalıkların beklenmedik şekilde yükselmesine neden olur. Güvenliğe güvenli kritik kod, ciddi bir güvenlik denetimine gitmelidir. **Note:**  Güvenlik açısından kritik olan türler ve Üyeler, çağıranın korumalı kaynaklara erişme yetkisi olup olmadığını belirlemede çağıranların izinlerini doğrulamalıdır.|  
  
 <xref:System.Security.SecuritySafeCriticalAttribute> özniteliği, güvenlik açısından saydam kodun aynı derlemede bulunan güvenlik açısından kritik üyelere erişmesine olanak sağlar. Derlemelerinizdeki güvenlik açısından saydam ve kritik güvenlik kodunu iki derlemeye ayırarak göz önünde bulundurun. Güvenliği saydam kod, güvenlik açısından kritik kodun özel veya iç üyelerini göremez. Ayrıca, güvenlik açısından kritik kod genel arabirimine erişim için genellikle denetlenir. Özel veya iç durumun derleme dışında erişilebilir olması beklenmez; durumu yalıtılmış tutmak isteyebilirsiniz. <xref:System.Security.SecuritySafeCriticalAttribute> özniteliği, gerektiğinde yalıtımın geçersiz kılınmasına izin verirken, güvenlik açısından saydam ve güvenlik açısından kritik kod arasındaki durumun yalıtımının tutulmasını sağlar. Bu Üyeler <xref:System.Security.SecuritySafeCriticalAttribute>olarak işaretlenmedikçe, güvenlik açısından saydam kod özel veya iç güvenlik açısından kritik koda erişemez. <xref:System.Security.SecuritySafeCriticalAttribute>uygulamadan önce, bu üyeyi genel kullanıma sunulmiş gibi denetleyin.  
  
### <a name="assembly-wide-annotation"></a>Bütünleştirilmiş kod genelinde ek açıklama  
 Aşağıdaki tabloda, derleme düzeyinde güvenlik özniteliklerini kullanmanın etkileri açıklanmaktadır.  
  
|Derleme özniteliği|Derleme durumu|  
|------------------------|--------------------|  
|Kısmen güvenilen bir derlemede öznitelik yok|Tüm türler ve Üyeler saydamdır.|  
|Tam güvenilir bir derlemede (genel derleme önbelleğinde veya `AppDomain`tam güven olarak tanımlanan) öznitelik yok|Tüm türler saydamdır ve tüm Üyeler güvenlik açısından güvenlidir.|  
|`SecurityTransparent`|Tüm türler ve Üyeler saydamdır.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Tüm türler ve Üyeler güvenlik açısından kritik öneme sahiptir.|  
|`SecurityCritical`|Tüm kod varsayılan olarak saydam olur. Ancak, ayrı türler ve üyelerin diğer öznitelikleri olabilir.|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a>Güvenlik saydamlığı örnekleri  
 .NET Framework 2,0 saydamlık kurallarını (düzey 1 saydamlık) kullanmak için aşağıdaki derleme ek açıklamasını kullanın:  
  
```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Derlemenin herhangi bir kritik kod içermediğini ve ayrıcalıkları herhangi bir şekilde yükselmediğini belirtmek için bir derlemenin tamamını saydam hale getirmek isterseniz, aşağıdaki öznitelik ile derlemeye açıkça saydamlık ekleyebilirsiniz:  
  
```csharp  
[assembly: SecurityTransparent]  
```  
  
 Aynı derlemede kritik ve saydam kodu karıştırmak istiyorsanız, derlemenin önemli kodu içerebileceğini belirtmek için derlemeyi <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle işaretleyerek başlayın:  
  
```csharp  
[assembly: SecurityCritical]  
```  
  
 Güvenlik açısından kritik eylemler gerçekleştirmek istiyorsanız, aşağıdaki kod örneğinde gösterildiği gibi, kritik eylemi gerçekleştirecek kodu başka bir <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle birlikte açıkça işaretlemeniz gerekir:  
  
```csharp  
[assembly: SecurityCritical]  
public class A  
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
  
 Önceki kod, açıkça güvenlik açısından kritik olarak işaretlenen `Critical` yöntemi dışında saydamdır. Saydamlık, derleme düzeyi <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle bile varsayılan ayardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliği saydam kod, düzey 2](security-transparent-code-level-2.md)
- [Güvenlik Değişiklikleri](../security/security-changes.md)
