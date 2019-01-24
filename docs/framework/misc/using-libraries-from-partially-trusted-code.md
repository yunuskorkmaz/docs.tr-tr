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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d32e5ed28153ae3ad54e1f75242a767d2e764a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585282"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Kısmen Güvenilen Koddan Kitaplıkları Kullanma
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  Bu konu, tanımlayıcı adlı derlemeler davranışını yöneliktir ve yalnızca geçerli [düzey 1](../../../docs/framework/misc/security-transparent-code-level-1.md) derlemeler. [Güvenliği saydam kod, 2. düzey](../../../docs/framework/misc/security-transparent-code-level-2.md) derlemelerde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] veya üzeri tanımlayıcı adlar tarafından etkilenmez. Güvenlik sistemine yapılan değişiklikler hakkında daha fazla bilgi için bkz. [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
 Paylaşılan çağırmak için tam güven konak ya da korumalı alan izin verilmez daha az alan uygulamalar yönetilen kitaplıkları kitaplığı yazıcı özellikle kullanımının kendisine izin vermediği sürece <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği. Bu nedenle, uygulama yazarları bazı kitaplıklar kendisine kısmen güvenilen bağlamından kullanılabilir olmayacağını farkında olmanız gerekir. Varsayılan olarak, tüm kod, yürütür kısmi güven [korumalı alan](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) ve de tam güven derleme listesini kısmen güvenilir değil. Kısmen güvenilen bir bağlamdan yürütülecek veya kısmen güvenilen kod tarafından çağrılmak için kodunuzu düşünmüyorsanız bu bölümdeki bilgiler hakkında merak gerekmez. Ancak, kısmen güvenilen bir bağlamdan gerekir ya da kısmen güvenilen kod ile etkileşim çalışmasına bir kod yazarsanız, aşağıdaki faktörleri dikkate almanız gerekir:  
  
-   Kitaplıkları birden çok uygulama tarafından paylaşılacak için tanımlayıcı ad ile imzalanması gerekir. Güçlü adlar izin genel bütünleştirilmiş kod önbelleğine yerleştirilen ya da tam güven listesine bir korumalı alana alma, kodunuzu <xref:System.AppDomain>, ve tüketiciler, belirli bir mobil kod parçasını gerçekten sizden kaynağının olduğunu doğrulamak izin verir.  
  
-   Varsayılan olarak, güçlü adlı [düzey 1](../../../docs/framework/misc/security-transparent-code-level-1.md) paylaşılan kitaplıklar gerçekleştirmek örtük [LinkDemand](../../../docs/framework/misc/link-demands.md) için tam güven otomatik olarak herhangi bir şey yapmanıza gerek kalmadan kitaplığı yazıcı.  
  
-   Bir çağıranın tam güven yok ancak yine de bir tür kitaplığı çağırmayı dener, çalışma zamanı oluşturur bir <xref:System.Security.SecurityException> çağıran Kitaplığı'na bağlamak için izin verilmez.  
  
-   Otomatik devre dışı bırakmak için **LinkDemand** ve oluşturulan gelen özel durumu engellersiniz, koyabilirsiniz **AllowPartiallyTrustedCallersAttribute** paylaşılan bir derleme kapsamı özniteliği Kitaplığı. Bu öznitelik, yönetilen kısmen güvenilen koddan çağrılan Kitaplıklarınızı sağlar.  
  
-   Bu öznitelik bir kitaplıkla erişim izni kısmen güvenilen kod tarafından tanımlanan yine de sınırlamalar tabidir <xref:System.AppDomain>.  
  
-   Sahip olmayan bir kitaplık çağrılacak kısmen güvenilen kod için programlı hiçbir yolu yoktur **AllowPartiallyTrustedCallersAttribute** özniteliği.  
  
 Belirli bir uygulamaya özel kitaplıkları, tanımlayıcı ad gerekmez veya **AllowPartiallyTrustedCallersAttribute** özniteliği ve uygulama dışında kötü amaçlı kod tarafından başvurulamaz. Bu kod, ekstra bir şey yapmanıza gerek kalmadan Geliştirici mobil kısmen güvenilen kod tarafından kasıtlı veya kasıtsız kötüye karşı korunur.  
  
 Açıkça kod aşağıdaki türde kısmen güvenilen kod tarafından kullanım etkinleştirme dikkate almanız gerekir:  
  
-   Güvenlik açıkları için titizlikle test edilmiştir ve nda açıklanan yönergelere uygun olan kod [güvenli kodlama kılavuzları](../../../docs/standard/security/secure-coding-guidelines.md).  
  
-   Kısmen güvenilen senaryoları için özel olarak yazılmış kesin adlandırılmış kod kitaplıkları.  
  
-   Tüm bileşenleri (kısmen veya tamamen güvenilir olup olmadığını) Internet'ten indirilen kod tarafından çağrılacak bir tanımlayıcı ad ile imzalanmış.  
  
> [!NOTE]
>  .NET Framework sınıf kitaplığındaki bazı sınıflar olmadığı **AllowPartiallyTrustedCallersAttribute** özniteliği ve kısmen güvenilen kod tarafından çağrılamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)
