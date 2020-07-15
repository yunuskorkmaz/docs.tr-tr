---
title: Kısmen Güvenilen Koddan Kitaplıkları Kullanma
description: Kısmen güvenilen koddan kitaplıkların nasıl kullanılacağını öğrenin. Paylaşılan yönetilen kitaplıkları çağırmak için AllowPartiallyTrustedCallersAttribute özniteliğini kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
ms.openlocfilehash: d2e015e381a3778bbab9977af20897ce9f1955c1
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309228"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Kısmen Güvenilen Koddan Kitaplıkları Kullanma
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> Bu konu, tanımlayıcı adlı derlemelerin davranışını ele almaktadır ve yalnızca [düzey 1](security-transparent-code-level-1.md) derlemeler için geçerlidir. [Güvenlik açısından saydam kod,](security-transparent-code-level-2.md) .NET Framework 4 veya sonraki sürümlerde düzey 2 derlemeleri tanımlayıcı adlarla etkilenmez. Güvenlik sisteminde yapılan değişiklikler hakkında daha fazla bilgi için bkz. [güvenlik değişiklikleri](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Kitaplık yazıcısı özel olarak özniteliğin kullanımına izin vermedikleri takdirde, ana bilgisayar veya korumalı kuruluşlarının tam güveninden daha az alan uygulamaların paylaşılan yönetilen kitaplıkları çağırmalarına izin verilmez <xref:System.Security.AllowPartiallyTrustedCallersAttribute> . Bu nedenle, uygulama yazarları bazı kitaplıkların kısmen güvenilen bağlamdan edinilemeyeceği farkında olmalıdır. Varsayılan olarak, kısmi güven [korumalı](how-to-run-partially-trusted-code-in-a-sandbox.md) alanında yürütülen ve tam güven derlemeleri listesinde olmayan tüm kodlar kısmen güvenilirdir. Kodunuzun kısmen güvenilen bir içerikten yürütülmesini veya kısmen güvenilen kod tarafından çağrılması beklenmiyorsa, bu bölümdeki bilgilerle ilgilenmeniz gerekmez. Ancak kısmen güvenilen kodla etkileşimde bulunmak zorunda olan veya kısmen güvenilen bağlamdan çalışan bir kod yazarsanız, aşağıdaki faktörleri göz önünde bulundurmanız gerekir:  
  
- Kitaplıkların birden çok uygulama tarafından paylaşılması için bir tanımlayıcı ad ile imzalanması gerekir. Güçlü adlar, kodunuzun genel derleme önbelleğine yerleştirilmesine veya bir korumalı alana alma tam güven listesine eklenmiş olmasını sağlar <xref:System.AppDomain> ve tüketicilere, belirli bir mobil kod parçasının gerçekten sizin için kaynak olduğunu doğrulamasına izin verir.  
  
- Varsayılan olarak, tanımlayıcı adlı [düzey 1](security-transparent-code-level-1.md) paylaşılan kitaplıklar, kitaplık yazarının hiçbir şey yapmasına gerek kalmadan otomatik olarak tam güven için örtük bir [LinkDemand](link-demands.md) gerçekleştirir.  
  
- Çağıran, tam güvene sahip değilse ancak yine de böyle bir kitaplığı çağırmaya çalışırsa, çalışma zamanı bir oluşturur <xref:System.Security.SecurityException> ve çağıranın kitaplığa bağlantı yapmasına izin verilmez.  
  
- Otomatik **LinkDemand** 'ı devre dışı bırakmak ve özel durumun oluşmasını engellemek Için, **AllowPartiallyTrustedCallersAttribute** özniteliğini paylaşılan bir kitaplığın derleme kapsamına yerleştirebilirsiniz. Bu öznitelik, kitaplıklarınızın kısmen güvenilen yönetilen koddan çağrılmasına izin verir.  
  
- Bu özniteliğe sahip bir kitaplığa erişim izni verilen kısmen güvenilen kod, tarafından tanımlanan daha fazla kısıtlamayla hala tabidir <xref:System.AppDomain> .  
  
- Kısmen güvenilen kodun **AllowPartiallyTrustedCallersAttribute** özniteliğine sahip olmayan bir kitaplığı çağırması için programlı bir yol yoktur.  
  
 Belirli bir uygulamaya özel olan kitaplıklar için bir tanımlayıcı ad veya **AllowPartiallyTrustedCallersAttribute** özniteliği gerekmez ve uygulama dışında olabilecek kötü amaçlı kod tarafından başvurulamaz. Bu kod, geliştiricilerin ek bir şey yapmasına gerek kalmadan kısmen güvenilen mobil kod tarafından kasıtlı olarak veya istemeden kötüye kullanılmasına karşı korunur.  
  
 Aşağıdaki kod türleri için kısmen güvenilen kod tarafından kullanımını açıkça etkinleştirmeyi düşünmelisiniz:  
  
- Güvenlik açıklarına karşı bir şekilde sınanmış ve [güvenli kodlama yönergeleri](../../standard/security/secure-coding-guidelines.md)bölümünde açıklanan kılavuzlarla uyumlu olan kod.  
  
- Kısmen güvenilen senaryolar için özel olarak yazılmış tanımlayıcı adlandırılmış kod kitaplıkları.  
  
- Internet 'ten indirilen kod tarafından çağrılacak bir tanımlayıcı ad ile imzalanmış olan tüm bileşenler (kısmen veya tamamen güvenilir olsun).  
  
> [!NOTE]
> .NET Framework sınıf kitaplığındaki bazı sınıfların **AllowPartiallyTrustedCallersAttribute** özniteliği yok ve kısmen güvenilen kod tarafından çağrılamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kod Erişimi Güvenliği](code-access-security.md)
