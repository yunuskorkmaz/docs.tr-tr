---
title: Kısmen Güvenilen Koddan Kitaplıkları Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
ms.openlocfilehash: 61291a07639c3f92a05f78dff49f6b20f1aee77e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645713"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Kısmen Güvenilen Koddan Kitaplıkları Kullanma
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> Bu konu, güçlü adlandırılmış derlemelerin davranışını ele adatır ve yalnızca [Düzey 1](security-transparent-code-level-1.md) derlemeleri için geçerlidir. [Güvenlik Saydam Kod, Düzey 2](security-transparent-code-level-2.md) derlemeleri .NET Framework 4 veya sonraki güçlü adlar etkilenmez. Güvenlik sistemindeki değişiklikler hakkında daha fazla bilgi için [Güvenlik Değişiklikleri'ne](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)bakın.  
  
 Ana bilgisayarlarından veya sandbox'larından tam güvenden daha az ını alan uygulamaların, kitaplık yazarı özellikle <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliğin kullanımına izin verilmedikçe paylaşılan yönetilen kitaplıkları aramasına izin verilmez. Bu nedenle, uygulama yazarları bazı kitaplıklar kısmen güvenilen bir bağlamda niçin kullanılabilir olmayacağını farkında olmalıdır. Varsayılan olarak, kısmi güven [sandbox'ta](how-to-run-partially-trusted-code-in-a-sandbox.md) yürüten ve tam güven derlemeleri listesinde olmayan tüm kodlara kısmen güvenilir. Kodunuzu kısmen güvenilen bir bağlamdan yürütülmesini veya kısmen güvenilen kod tarafından çağrılmasını beklemiyorsanız, bu bölümdeki bilgilerle ilgilenmeniz gerekmez. Ancak, kısmen güvenilen kodla etkileşimde olması veya kısmen güvenilen bir bağlamdan çalışması gereken kod yazarsanız, aşağıdaki faktörleri göz önünde bulundurmanız gerekir:  
  
- Birden çok uygulama tarafından paylaşılabilmesi için kitaplıkların güçlü bir adla imzalanması gerekir. Güçlü adlar, kodunuzu genel montaj önbelleğine yerleştirilmesine veya bir kum <xref:System.AppDomain>kutulamanın tam güven listesine eklenmesine ve tüketicilerin belirli bir mobil kodun aslında sizden geldiğini doğrulamasına olanak sağlar.  
  
- Varsayılan olarak, güçlü adlandırılmış [Düzey 1](security-transparent-code-level-1.md) paylaşılan kitaplıklar, kitaplık yazarının hiçbir şey yapmasına gerek kalmadan otomatik olarak tam güven için örtülü bir [Bağlantı İsteği](link-demands.md) gerçekleştirir.  
  
- Bir arayan tam güvene sahip değilse ancak yine de böyle bir <xref:System.Security.SecurityException> kitaplığı aramaya çalışırsa, çalışma zamanı bir atar ve arayanın kitaplık la bağlanmasına izin verilmez.  
  
- Otomatik **LinkDemand'ı** devre dışı bırakıp özel durum atılmasını önlemek **için, AllowPartiallyTrustedCallersAttribute özniteliğini** paylaşılan kitaplığın derleme kapsamına yerleştirebilirsiniz. Bu öznitelik, kitaplıklarınızın kısmen güvenilen yönetilen koddan çağrılmasını sağlar.  
  
- Bu öznitelik ile bir kitaplık erişim verilen kısmen güvenilen kod hala <xref:System.AppDomain>tarafından tanımlanan diğer kısıtlamalara tabidir .  
  
- Kısmen güvenilen kodun **AllowPartiallyTrustedCallersAttribute özniteliği** olmayan bir kitaplığı çağırmasının programlı bir yolu yoktur.  
  
 Belirli bir uygulamaya özel olan kitaplıklar güçlü bir ad veya **AllowPartiallyTrustedCallersAttribute** özniteliği gerektirmez ve uygulama dışında kötü amaçlı olabilecek kodla başvurulamıyor. Bu kod, geliştirici ekstra bir şey yapmak zorunda kalmadan kısmen güvenilen mobil kod tarafından kasıtlı veya kasıtsız kötüye kullanımına karşı korunur.  
  
 Aşağıdaki kod türleri için kısmen güvenilen kod tarafından kullanımı açıkça etkinleştirmeyi düşünmelisiniz:  
  
- Güvenlik açıkları için özenle test edilmiş ve Güvenli Kodlama Yönergeleri'nde açıklanan yönergelere uygun olan [kod.](../../standard/security/secure-coding-guidelines.md)  
  
- Kısmen güvenilen senaryolar için özel olarak yazılmış güçlü adlandırılmış kod kitaplıkları.  
  
- Internet'ten indirilen kodla çağrılacak güçlü bir adla imzalanan tüm bileşenler (kısmen veya tamamen güvenilir olsun).  
  
> [!NOTE]
> .NET Framework sınıf kitaplığındaki bazı **sınıflarAllowPartiallyTrustedCallersAtöz** özniteliğine sahip değildir ve kısmen güvenilen kod tarafından çağrılmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kod Erişimi Güvenliği](code-access-security.md)
