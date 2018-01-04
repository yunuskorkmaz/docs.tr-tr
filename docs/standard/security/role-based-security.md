---
title: "Rol Tabanlı Güvenlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET Framework]
- security [.NET Framework], role-based
- permissions [.NET Framework], principals
- authentication [.NET Framework], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 18b2883fd69f5cadf2fce3dc677e5d2b79806d0b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="role-based-security"></a>Rol Tabanlı Güvenlik
Roller, genellikle ilkeyi uygulamak için finans veya iş uygulamalarında kullanılır. Örneğin, bir uygulama, istekte bulunan kullanıcının belirtilen bir rol üyesi olup bağlı olarak işlenmekte olan işlem boyutu sınırları zorunlu tuttukları. Belirtilen eşikten daha az işlem işlemler için yetkilendirme elemanı olabilir, daha yüksek bir sınır denetçiler olabilir ve yardımcısının Yardımcıları hala daha yüksek bir sınır (veya hiç sınır) olabilir. Bir uygulama bir eylemi tamamlamak için birden çok onayları gerektirdiğinde rol tabanlı güvenlik de kullanılabilir. Böyle bir durumda çalışan bir satın alma isteği üretebilir bir satın alma sistemi olabilir, ancak yalnızca bir satın alma Aracısı bu isteği bir tedarikçiye gönderilebilecek bir satın alma siparişi dönüştürebilirsiniz.  
  
 .NET framework rol tabanlı güvenlik, geçerli iş parçacığının kullanılabilir ilişkili bir kimlik gelen oluşturulan asıl hakkında bilgi yaparak yetkilendirme destekler. Kimliği (ve tanımlamak için yardımcı asıl) üzerinde bir Windows hesabı ya da bağlı olabilir veya bir Windows hesabı ilgisi olmayan özel bir kimlik. .NET framework uygulamaları sorumlusunun kimliğini veya rol üyeliğini veya her ikisi de dayalı yetkilendirme kararlarını verebilir. Bir rol aynı ayrıcalıklarınız (örneğin, bir teller veya Yöneticisi) güvenlik göre ilkeleri adlandırılmış kümesidir. Sorumlu bir veya daha fazla rollerinin bir üyesi olabilir. Bu nedenle, uygulamalar, rol üyeliğini sorumlu istenen eylemi gerçekleştirmek için yetkili olup olmadığını belirlemek için kullanabilirsiniz.  
  
 Kod erişim güvenliği ile kullanım kolaylığı ve tutarlılığı sağlamak için .NET Framework rol tabanlı güvenlik sağlar <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> yetkilendirme kodu benzer bir şekilde gerçekleştirmek ortak dil çalışma zamanı etkinleştirme nesneleri erişim güvenlik denetimleri. <xref:System.Security.Permissions.PrincipalPermission> Kimlik veya asıl eşleşmelidir ve her iki bildirim temelli ve kesinlik temelli güvenlik denetimleri ile uyumlu olan rol sınıfı temsil eder. Ayrıca bir sorumlunun kimlik bilgilerini doğrudan erişmek ve rol gerçekleştirmek ve gerektiğinde kodunuzda kimlik denetler.  
  
 .NET Framework esnek ve uygulamaları geniş bir yelpazesini ihtiyaçlarını karşılamak üzere yeterli Genişletilebilir rol tabanlı güvenlik desteği sağlar. COM + 1.0 Hizmetleri gibi varolan kimlik doğrulama altyapılar birlikte çalışmanız veya bir özel kimlik doğrulama sistemi oluşturmak için seçebilirsiniz. Rol tabanlı güvenlik özellikle çok öncelikle sunucuda işlenir ASP.NET Web uygulamalarında kullanım için uygundur. Ancak, .NET Framework rol tabanlı güvenlik, istemci veya sunucu üzerinde kullanılabilir.  
  
 Bu bölümü okumadan önce içinde sunulan malzeme anladığınızdan emin olun [temel güvenlik kavramları](../../../docs/standard/security/key-security-concepts.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Sorumlu ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)|Windows ve genel kimlikleri ve ilkeleri ayarlamanıza açıklanmaktadır.|  
|[Temel Güvenlik Kavramları](../../../docs/standard/security/key-security-concepts.md)|.NET Framework güvenliği kullanmadan önce anlamanız gereken temel kavramlar tanıtılmaktadır.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
