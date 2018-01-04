---
title: "Kısmen Güvenilen Koddan Kitaplıkları Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00f532e4e93936dbd719f2b8a0c060e54e16425b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-libraries-from-partially-trusted-code"></a>Kısmen Güvenilen Koddan Kitaplıkları Kullanma
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  Bu konuda tanımlayıcı adlı derlemeler davranışını yöneliktir ve yalnızca geçerli [düzey 1](../../../docs/framework/misc/security-transparent-code-level-1.md) derlemeler. [Güvenliği saydam kod, Düzey 2](../../../docs/framework/misc/security-transparent-code-level-2.md) derlemelerde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] veya üzeri tanımlayıcı adlar tarafından etkilenmez. Güvenlik sistemi değişiklikler hakkında daha fazla bilgi için bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
 Paylaşılan çağırmak için tam güven kendi ana bilgisayardan veya korumalı alan verilmez daha az alan uygulamalar yönetilen kitaplıkları kitaplığı yazan özellikle kullanım yoluyla kendisine izin vermediği sürece <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği. Bu nedenle, uygulama yazarları bazı kitaplıklar onlara kısmen güvenilen bağlamından kullanılabilir olmayacağını farkında olmanız gerekir. Varsayılan olarak, tüm kod yürütmelerinin kısmi güvende [korumalı alan](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) ve buna tam güven derleme listesi kısmen güvenilir değil. Kısmen güvenilen bağlamından yürütülecek veya kısmen güvenilen kod tarafından çağrılacak kodunuzu düşünmüyorsanız bu bölümdeki bilgiler hakkında endişelenmeniz gerekmez. Ancak, kısmen güvenilen bağlamından kısmen güvenilen kodla etkileşim veya çalışması gerekir kodu yazarsanız, aşağıdaki etmenleri düşünmeniz gerekir:  
  
-   Kitaplıklar, birden çok uygulama tarafından paylaşılması için tanımlayıcı bir ad ile imzalanmalıdır. Tanımlayıcı adlar izin genel derleme önbelleğinde yerleştirilen veya tam güven listesine bir korumalı alan, kodunuzun <xref:System.AppDomain>, ve belirli bir mobil kod gerçekten sizden kaynağının olduğunu doğrulamak tüketicilere izin verin.  
  
-   Varsayılan olarak, tanımlayıcı adlı [düzey 1](../../../docs/framework/misc/security-transparent-code-level-1.md) paylaşılan kitaplıklar gerçekleştirmek örtülü [LinkDemand](../../../docs/framework/misc/link-demands.md) için tam güven otomatik olarak, herhangi bir şey yapmanıza gerek kalmadan kitaplığı yazan.  
  
-   Çağıran tam güven yok ancak yine de bu tür bir kitaplık çağırmayı dener, çalışma zamanı döndürürse bir <xref:System.Security.SecurityException> ve arayan Kitaplığı'na bağlamak için izin verilmiyor.  
  
-   Otomatik devre dışı bırakmak için **LinkDemand** ve oluşturulan gelen özel durum önlemek için yerleştireceğiniz **AllowPartiallyTrustedCallersAttribute** paylaşılan derleme kapsamını özniteliği Kitaplığı. Bu öznitelik Kitaplıklarınızı kısmen güvenilen yönetilen koddan çağrılan sağlar.  
  
-   Bu öznitelik bir kitaplıkla erişim izni kısmen güvenilen kod tarafından tanımlanan hala sınırlamalar tabidir <xref:System.AppDomain>.  
  
-   Hiçbir programlı şekilde sahip olmayan bir kitaplık çağrılacak kısmen güvenilen kod için **AllowPartiallyTrustedCallersAttribute** özniteliği.  
  
 Belirli bir uygulamaya özel kitaplıkları bir güçlü ad gerekli olmadığı veya **AllowPartiallyTrustedCallersAttribute** özniteliği ve uygulama dışında kötü amaçlı kodlar tarafından başvurulamaz. Bu tür kodu kasıtlı olarak veya yanlışlıkla kötüye karşı ek bir şey yapmanıza gerek kalmadan Geliştirici mobil kısmen güvenilen kod tarafından korunur.  
  
 Açıkça kod aşağıdaki türleri için kısmen güvenilen kod tarafından kullanım etkinleştirmeyi düşünebilirsiniz:  
  
-   Güvenlik açıklarını titizlikle test edilmiştir ve açıklanan yönergeleri uyumlu olan kodu [güvenli kodlama yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md).  
  
-   Kısmen güvenilen senaryoları için özel olarak yazılmış tanımlayıcı adlı kodu kitaplıkları.  
  
-   Tüm bileşenleri (kısmen veya tamamen güvenilir olup olmadığını) Internet'ten indirilen kod tarafından çağrılan bir güçlü ad ile imzalanmış.  
  
> [!NOTE]
>  .NET Framework Sınıf Kitaplığı'nda bazı sınıfları olmadığı **AllowPartiallyTrustedCallersAttribute** özniteliği ve kısmen güvenilen kod tarafından çağrılamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)
