---
title: Rol Tabanlı Güvenlik
ms.date: 07/15/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET]
- security [.NET], role-based
- permissions [.NET], principals
- authentication [.NET], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
ms.openlocfilehash: ed6c33be5a5da066e238c160da8bff8d25cb68fc
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555687"
---
# <a name="role-based-security"></a>Rol Tabanlı Güvenlik

Roller, ilkeyi zorlamak için genellikle finansal veya iş uygulamalarında kullanılır. Örneğin, bir uygulama, istekte bulunan kullanıcının belirtilen bir rolün üyesi olup olmadığına bağlı olarak işlenen işlemin boyutuna yönelik sınırlar uygulayabilir. Büro 'lar, belirtilen eşikten daha az olan işlemleri işlemek için yetkilendirmeye yetki verebilir, süper vizörlerin daha yüksek bir sınırı olabilir ve başkanlardan de daha yüksek bir sınıra sahip olabilir (veya hiç sınır yoktur). Rol tabanlı güvenlik, bir uygulamanın bir eylemi tamamlaması için birden fazla onay gerektirmesi durumunda da kullanılabilir. Böyle bir durum, herhangi bir çalışanın bir satın alma isteği oluşturabileceği bir satın alma sistemi olabilir, ancak yalnızca bir satın alma aracısı bu talebi bir tedarikçiye gönderilebilecek bir satın alma siparişine dönüştürebilir.  
  
 .NET rol tabanlı güvenlik, geçerli iş parçacığı tarafından kullanılabilen, ilişkili bir kimlikle oluşturulan sorumlu hakkında bilgi sunarak yetkilendirmeyi destekler. Kimlik (ve tanımlamaya yardımcı olan asıl), bir Windows hesabına göre veya bir Windows hesabıyla ilgisi olmayan özel bir kimlik olabilir. .NET uygulamaları, sorumlu kimlik veya rol üyeliğine veya her ikisine göre yetkilendirme kararları verebilir. Rol, güvenlikle ilgili olarak aynı ayrıcalıklara sahip olan (örneğin, bir teller veya yönetici), adlandırılmış bir sorumlu kümesidir. Bir sorumlu bir veya daha fazla rolün üyesi olabilir. Bu nedenle, uygulamalar, bir sorumlunun istenen eylemi gerçekleştirme yetkisine sahip olup olmadığını anlamak için rol üyeliğini kullanabilir.  
  
 Kod erişim güvenliği ile kullanım kolaylığı ve tutarlılığı sağlamak için, .NET rol tabanlı güvenlik, <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> ortak dil çalışma zamanının, kimlik doğrulama erişimi güvenlik denetimlerine benzer bir şekilde gerçekleştirmesini sağlayan nesneler sağlar. <xref:System.Security.Permissions.PrincipalPermission>Sınıfı, sorumlunun eşleşmesi gereken kimliği veya rolü temsil eder ve hem bildirime dayalı hem de zorunlu güvenlik denetimleri ile uyumludur. Ayrıca, bir sorumlu kimlik bilgilerine doğrudan erişebilir ve gerektiğinde kodunuzda rol ve kimlik denetimleri gerçekleştirebilirsiniz.  
  
 .NET, esnek ve geniş bir uygulama yelpazesini karşılamak için yeterince Genişletilebilir rol tabanlı güvenlik desteği sağlar. COM+ 1,0 hizmetleri gibi mevcut kimlik doğrulama altyapılarla birlikte çalışabilme veya özel bir kimlik doğrulama sistemi oluşturma seçeneğini belirleyebilirsiniz. Rol tabanlı güvenlik, özellikle sunucuda işlenen ASP.NET Web uygulamalarında kullanım için uygun bir seçenektir. Ancak, .NET rol tabanlı güvenlik, istemci ya da sunucu üzerinde kullanılabilir.  
  
 Bu bölümü okumadan önce, [anahtar güvenlik kavramları](key-security-concepts.md)bölümünde sunulan malzemeleri anladığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.
  
- [Asıl ve Kimlik Nesneleri](principal-and-identity-objects.md)
- [Temel Güvenlik Kavramları](key-security-concepts.md)
- <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
- [ASP.NET Core güvenliği](/aspnet/core/security/)
