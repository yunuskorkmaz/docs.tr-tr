---
title: Güvenlik-Saydam Kod, Düzey 1
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
ms.openlocfilehash: 980c684bced685a61ad82ff5713ccff2b974028f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181124"
---
# <a name="security-transparent-code-level-1"></a>Güvenlik-Saydam Kod, Düzey 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Saydamlık, geliştiricilerin işlevselliği kısmen güvenilen koda maruz bırakan daha güvenli .NET Framework kitaplıkları yazmalarına yardımcı olur. Düzey 1 saydamlığı .NET Framework sürüm 2.0'da tanıtıldı ve öncelikle yalnızca Microsoft içinde kullanıldı. .NET Framework 4'ten başlayarak [düzey 2 saydamlığı](security-transparent-code-level-2.md)kullanabilirsiniz. Ancak, önceki güvenlik kurallarıyla çalışması gereken eski kodu tanımlayabilmeniz için düzey 1 saydamlığı korunmuştur.  
  
> [!IMPORTANT]
> Yalnızca uyumluluk için düzey 1 saydamlık belirtmeniz gerekir; diğer bir şey, düzey 1'i yalnızca .NET Framework 3.5 veya <xref:System.Security.AllowPartiallyTrustedCallersAttribute> önceki saydamlık modelini kullanan veya kullanmayan kod için belirtin. Örneğin, kısmen güvenilen arayanlardan (APTCA) gelen çağrılara izin veren .NET Framework 2.0 derlemeleri için düzey 1 saydamlığı kullanın. .NET Framework 4 için geliştirilen kod için her zaman düzey 2 saydamlığı kullanın.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Düzey 1 Saydamlık Modeli](#the_level_1_transparency_model)  
  
- [Saydamlık Öznitelikleri](#transparency_attributes)  
  
- [Güvenlik Şeffaflığı Örnekleri](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>
## <a name="the-level-1-transparency-model"></a>Düzey 1 Saydamlık Modeli  
 Düzey 1 saydamlık kullandığınızda, kodu güvenlik saydamlığı, güvenlik açısından kritik ve güvenlik açısından kritik yöntemlere ayıran bir güvenlik modeli kullanırsınız.  
  
 Tüm derlemeyi, derlemedeki bazı sınıfları veya bir sınıftaki bazı yöntemleri güvenlik saydamolarak işaretleyebilirsiniz. Güvenlik saydam kod ayrıcalıkları yükseltemez. Bu kısıtlamanın üç sonucu vardır:  
  
- Güvenlik saydam kod <xref:System.Security.Permissions.SecurityAction.Assert> eylemleri gerçekleştiremez.  
  
- Güvenlik saydam kodu tarafından karşılanacak herhangi bir bağlantı talebi tam bir talep haline gelir.  
  
- Güvenlik saydam kodda yürütülmesi gereken güvenli olmayan (doğrulanamayan) kod, <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> güvenlik izni için tam bir talep neden olur.  
  
 Bu kurallar, ortak dil çalışma zamanı (CLR) tarafından yürütme sırasında uygulanır. Güvenlik saydam kodu, aradığı kodun tüm güvenlik gereksinimlerini arayanlara geri geçirir. Güvenlik saydam kodundan geçen talepler ayrıcalıkları yükseltemez. Düşük güven uygulaması güvenlik saydam kodu çağırır ve yüksek ayrıcalık için bir talep neden olur, talep düşük güven koduna geri akacak ve başarısız olur. Güvenlik saydam kodu, iddialı eylemler gerçekleştiremediği için talebi durduramaz. Tam güven kodundan çağrılan aynı güvenlik saydam kodu, başarılı bir taleple sonuçlanır.  
  
 Güvenlik açısından kritik güvenlik saydamının tam tersidir. Güvenlik açısından kritik kod tam güvenle yürütülür ve tüm ayrıcalıklı işlemleri gerçekleştirebilir. Güvenlik açısından güvenli kritik kod, kısmen güvenilen arayanların erişim izni olmayan kaynakları kullanmalarına izin vermediğini doğrulamak için kapsamlı bir güvenlik denetimiyoluyla geçen ayrıcalıklı koddur.  
  
 Saydamlığı açıkça uygulamanız gerekir. Veri işleme ve mantık işleyen kodlarınızın çoğunluğu genellikle güvenlik saydam olarak işaretlenebilirken, ayrıcalıkların yükseltilerini gerçekleştiren daha az kod miktarı güvenlik açısından kritik veya güvenlik açısından güvenli kritik olarak işaretlenir.  
  
> [!IMPORTANT]
> Düzey 1 saydamlık montaj kapsamıyla sınırlıdır; derlemeler arasında zorlanmaz. Düzey 1 saydamlığı öncelikle Microsoft içinde güvenlik denetimi amacıyla kullanılmıştır. Düzey 1 derlemesi içindeki güvenlik açısından kritik türlere ve üyelere diğer derlemelerde güvenlik saydam koduyla erişilebilir. Tüm düzey 1 güvenlik açısından kritik türleri ve üyeleri tam güven için bağlantı taleplerini gerçekleştirmek önemlidir. Güvenlik açısından güvenli kritik türler ve üyeler, arayanların tür veya üye tarafından erişilen korumalı kaynaklar için izinleri olduğunu da onaylamalıdır.  
  
 .NET Framework'ün önceki sürümleriyle geriye dönük uyumluluk için, saydamlık öznitelikleriyle açıklama ekaçıklama lı olmayan tüm üyeler güvenlik açısından güvenli kritik olarak kabul edilir. Açıklamalı olmayan tüm türler saydam olarak kabul edilir. Saydamlığı doğrulamak için statik çözümleme kuralları yoktur. Bu nedenle, çalışma zamanında saydamlık hatalarını ayıklamanız gerekebilir.  
  
<a name="transparency_attributes"></a>
## <a name="transparency-attributes"></a>Saydamlık Öznitelikleri  
 Aşağıdaki tabloda, saydamlık için kodunuzu açıklama yapmak için kullandığınız üç öznitelik açıklanmaktadır.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Yalnızca montaj düzeyinde izin verilir. Derlemedeki tüm türleri ve üyeleri güvenlik saydamolarak tanımlar. Derleme herhangi bir güvenlik kritik kod içeremez.|  
|<xref:System.Security.SecurityCriticalAttribute>|<xref:System.Security.SecurityCriticalAttribute.Scope%2A> Özellik olmadan montaj düzeyinde kullanıldığında, varsayılan olarak derlemedeki tüm kodları güvenlik saydam olarak tanımlar, ancak derlemenin güvenlik açısından kritik kod içerebileceğini gösterir.<br /><br /> Sınıf düzeyinde kullanıldığında, sınıfı veya yöntemi güvenlik açısından kritik olarak tanımlar, ancak sınıfın üyeleri olarak değil. Tüm üyeleri güvenlik açısından kritik hale <xref:System.Security.SecurityCriticalAttribute.Scope%2A> getirmek <xref:System.Security.SecurityCriticalScope.Everything>için özelliği .<br /><br /> Üye düzeyinde kullanıldığında, öznitelik yalnızca bu üye için geçerlidir.<br /><br /> Güvenlik açısından kritik olarak tanımlanan sınıf veya üye ayrıcalık yükseklikleri gerçekleştirebilir. **Önemli:**  Düzey 1 saydamlık, güvenlik açısından kritik türleri ve üyeleri, montaj dışından çağrıldığında güvenlik açısından kritik olarak kabul edilir. Yetkisiz ayrıcalık yükselmesini önlemek için güvenlik açısından kritik türleri ve üyeleri tam güven için bir bağlantı talebiyle korumanız gerekir.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Derlemede güvenlik saydam kodu tarafından erişilebilen güvenlik açısından kritik kodu tanımlar. Aksi takdirde, güvenlik saydam kodu aynı derlemede özel veya iç güvenlik açısından kritik üyelere erişemez. Bunu yapmak, güvenlik açısından kritik kodu etkiler ve beklenmeyen ayrıcalık yükselmelerini mümkün kılar. Güvenlik açısından güvenli kritik kod sıkı bir güvenlik denetiminden geçmelidir. **Not:**  Güvenlik açısından güvenli kritik türler ve üyeler, arayanın korumalı kaynaklara erişme yetkisiolup olmadığını belirlemek için arayanların izinlerini doğrulamalıdır.|  
  
 Öznitelik, <xref:System.Security.SecuritySafeCriticalAttribute> güvenlik saydam kodunun aynı derlemede güvenlik açısından kritik üyelere erişmesini sağlar. Derlemenizdeki güvenlik saydam ve güvenlik açısından kritik kodu iki derlemeye ayrılmış olarak düşünün. Güvenlik saydam kodu, güvenlik açısından kritik kodun özel veya dahili üyelerini göremez. Ayrıca, güvenlik açısından kritik kod genel arabirimine erişim için genellikle denetlenir. Özel veya dahili bir devletin montaj dışında erişilebilir olmasını beklemezsiniz; Eyaleti izole etmek isterdin. Öznitelik, <xref:System.Security.SecuritySafeCriticalAttribute> gerektiğinde yalıtımı geçersiz kılma olanağı sağlarken, durum yalıtımını güvenlik saydamlığı ve güvenlik açısından kritik kod arasında tutar. Güvenlik saydam kodu, bu üyeler ile işaretlenmiş sürece özel veya <xref:System.Security.SecuritySafeCriticalAttribute>iç güvenlik kritik kod erişemez. Uygulamadan <xref:System.Security.SecuritySafeCriticalAttribute>önce, bu üyeyi kamuya açıklanmış gibi denetle.  
  
### <a name="assembly-wide-annotation"></a>Montaj genelinde Ek Açıklama  
 Aşağıdaki tabloda montaj düzeyinde güvenlik öznitelikleri kullanmanın etkileri açıklanmaktadır.  
  
|Montaj özniteliği|Meclis durumu|  
|------------------------|--------------------|  
|Kısmen güvenilen bir derlemede öznitelik yok|Tüm tür ve üyeler saydamdır.|  
|Tam olarak güvenilen bir derlemede öznitelik yok (genel montaj `AppDomain`önbelleğinde veya tam güven olarak tanımlanır)|Tüm türler saydamdır ve tüm üyeler güvenlik açısından kritik öneme sahiptir.|  
|`SecurityTransparent`|Tüm tür ve üyeler saydamdır.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Tüm türler ve üyeler güvenlik açısından kritik öneme sahiptir.|  
|`SecurityCritical`|Tüm kod varsayılan olarak saydamdır. Ancak, tek tek türleri ve üyeleri başka öznitelikleri olabilir.|  
  
<a name="security_transparency_examples"></a>
## <a name="security-transparency-examples"></a>Güvenlik Şeffaflığı Örnekleri  
 .NET Framework 2.0 saydamlık kurallarını (düzey 1 saydamlığı) kullanmak için aşağıdaki derleme ek açıklamasını kullanın:  
  
```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Derlemenin herhangi bir kritik kod içermediğini ve ayrıcalıkları herhangi bir şekilde yükseltmediğini belirtmek için tüm derlemeyi saydam hale getirmek istiyorsanız, derlemeye aşağıdaki öznitelik içeren saydamlık ekleyebilirsiniz:  
  
```csharp  
[assembly: SecurityTransparent]  
```  
  
 Kritik ve saydam kodu aynı derlemede karıştırmak istiyorsanız, derlemenin <xref:System.Security.SecurityCriticalAttribute> kritik kod içerebileceğini belirtmek için derlemeyi öznitelikile işaretleyerek başlayın:  
  
```csharp  
[assembly: SecurityCritical]  
```  
  
 Güvenlik açısından kritik eylemler gerçekleştirmek istiyorsanız, aşağıdaki kod örneğinde gösterildiği gibi, <xref:System.Security.SecurityCriticalAttribute> kritik eylemi gerçekleştirecek kodu başka bir öznitelikle açıkça işaretlemeniz gerekir:  
  
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
  
 Önceki kod, açıkça güvenlik `Critical` açısından kritik olarak işaretlenmiş yöntem dışında saydamdır. Saydamlık, derleme düzeyi <xref:System.Security.SecurityCriticalAttribute> özniteliği olsa bile varsayılan ayardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliği Saydam Kod, 2. Düzey](security-transparent-code-level-2.md)
- [Güvenlik Değişiklikleri](../security/security-changes.md)
