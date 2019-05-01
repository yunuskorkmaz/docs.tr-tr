---
title: Rol Tabanlı Güvenlik
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET Framework]
- security [.NET Framework], role-based
- permissions [.NET Framework], principals
- authentication [.NET Framework], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 596165bfac9c65898448714a4477b7f045bd87d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018586"
---
# <a name="role-based-security"></a>Rol Tabanlı Güvenlik
Rolleri, finansal veya iş uygulamalarında ilkeyi uygulamak için sık kullanılır. Örneğin, bir uygulama isteği yapan kullanıcının belirtilen rolünün bir üyesi olduğuna bağlı olarak işlenmekte olan işlem boyutu sınırı oluşturabileceğini. Belirtilen bir eşik değerinden düşük olan işlemleri işlemek için yetkilendirme elemanı olabilir, denetçilere daha yüksek bir sınıra sahip olmayabilir ve yardımcısının Başkan, hala daha yüksek bir sınır (veya hiç sınır yok) olabilir. Rol tabanlı güvenlik, uygulamanın bir eylemi tamamlamak için birden çok onay gerektirdiğinde de kullanılabilir. Böyle bir durumda çalışan bir satın alma isteği oluşturabilirsiniz bir satın alma sistemi olabilir, ancak yalnızca satın alma aracı bu istek için bir sağlayıcı gönderilebilecek bir satın alma siparişi dönüştürebilirsiniz.  
  
 .NET framework rol tabanlı güvenlik sorumlusu, geçerli iş parçacığı için kullanılabilir ilişkili bir kimlik nesnesinden oluşturulan hakkında bilgi sağlayarak yetkilendirme destekler. Kimlik (ve tanımlamak için yardımcı asıl) bir Windows hesabı ya da temel alabilir veya ilgisi olmayan bir Windows hesabı için özel bir kimlik. .NET framework uygulamaları, sorumlunun kimliğini veya rol üyeliğini veya her ikisi de göre yetkilendirme kararları hale getirebilirsiniz. Bir rol (örneğin, bir gişe veya Yöneticisi) güvenlik açısından aynı ayrıcalıklara sahip sorumluları adlandırılmış kümesidir. Bir sorumlunun bir veya daha fazla rollerinin bir üyesi olabilir. Bu nedenle, uygulamaları, rol üyeliğini bir sorumlunun istenen eylemi gerçekleştirmek için yetkili olup olmadığını belirlemek için kullanabilirsiniz.  
  
 Kod erişimi güvenliği kullanım kolaylığı ve tutarlılığı sağlamak için .NET Framework rol tabanlı güvenlik sağlar. <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> yetkilendirme koda benzer bir şekilde gerçekleştirmek ortak dil çalışma zamanını etkinleştirme nesneleri erişim güvenlik denetimleri. <xref:System.Security.Permissions.PrincipalPermission> Kimliği veya sorumlu eşleşmesi gerekir ve her iki bildirim temelli ve kesinlik temelli güvenlik denetimleri ile uyumlu olan rol sınıfı temsil eder. Ayrıca bir sorumlusunun kimlik bilgilerini doğrudan erişmek ve rol gerçekleştirmek ve gerektiğinde kodunuzda kimlik denetler.  
  
 .NET Framework, esnek ve çok geniş bir spektrumda uygulamalarının ihtiyaçlarını karşılamak için yeterli Genişletilebilir rol tabanlı güvenlik desteği sağlar. COM + 1.0 Hizmetleri gibi mevcut kimlik doğrulama altyapıları ile birlikte çalışmak veya bir özel kimlik doğrulama sistemi oluşturmak için seçebilirsiniz. Rol tabanlı güvenlik özellikle çok birincil sunucuda işlenir ASP.NET Web uygulamalarında kullanmak için uygundur. Ancak, .NET Framework rol tabanlı güvenlik, istemci veya sunucu üzerinde kullanılabilir.  
  
 Bu bölümü okumadan önce içinde sunulan malzeme anladığınızdan emin olun [temel güvenlik kavramları](../../../docs/standard/security/key-security-concepts.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Sorumlu ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)|Ayarlamanıza ve Windows ve genel kimlikleri ve ilkeleri yönetmenize olunacağı açıklanmaktadır.|  
|[Temel Güvenlik Kavramları](../../../docs/standard/security/key-security-concepts.md)|.NET Framework güvenlik kullanmadan önce anlamanız gereken temel kavramlar tanıtılmaktadır.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
