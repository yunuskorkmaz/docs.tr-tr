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
ms.openlocfilehash: 1dfb1f6246e86d6f565c9338fb09f34a1608e9b0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705931"
---
# <a name="role-based-security"></a>Rol Tabanlı Güvenlik
Roller, ilkeyi zorlamak için genellikle finansal veya iş uygulamalarında kullanılır. Örneğin, bir uygulama, istekte bulunan kullanıcının belirtilen bir rolün üyesi olup olmadığına bağlı olarak işlenen işlemin boyutuna yönelik sınırlar uygulayabilir. Büro 'lar, belirtilen eşikten daha az olan işlemleri işlemek için yetkilendirmeye yetki verebilir, süper vizörlerin daha yüksek bir sınırı olabilir ve başkanlardan de daha yüksek bir sınıra sahip olabilir (veya hiç sınır yoktur). Rol tabanlı güvenlik, bir uygulamanın bir eylemi tamamlaması için birden fazla onay gerektirmesi durumunda da kullanılabilir. Böyle bir durum, herhangi bir çalışanın bir satın alma isteği oluşturabileceği bir satın alma sistemi olabilir, ancak yalnızca bir satın alma aracısı bu talebi bir tedarikçiye gönderilebilecek bir satın alma siparişine dönüştürebilir.  
  
 Rol tabanlı güvenlik .NET Framework, geçerli iş parçacığı tarafından kullanılabilen, ilişkili bir kimlikle oluşturulan sorumlu hakkında bilgi vererek yetkilendirmeyi destekler. Kimlik (ve tanımlamaya yardımcı olan asıl), bir Windows hesabına göre veya bir Windows hesabıyla ilgisi olmayan özel bir kimlik olabilir. .NET Framework uygulamalar, sorumlu kimlik veya rol üyeliğine veya her ikisine göre yetkilendirme kararları verebilir. Rol, güvenlikle ilgili olarak aynı ayrıcalıklara sahip olan (örneğin, bir teller veya yönetici), adlandırılmış bir sorumlu kümesidir. Bir sorumlu bir veya daha fazla rolün üyesi olabilir. Bu nedenle, uygulamalar, bir sorumlunun istenen eylemi gerçekleştirme yetkisine sahip olup olmadığını anlamak için rol üyeliğini kullanabilir.  
  
 Kod erişim güvenliği ile kullanım kolaylığı ve tutarlılığı sağlamak için .NET Framework rol tabanlı güvenlik, ortak dil çalışma zamanının kimlik doğrulama erişimi güvenlik denetimlerine benzer bir şekilde gerçekleştirmesini sağlayan <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> nesneleri sağlar. <xref:System.Security.Permissions.PrincipalPermission> sınıfı, sorumlunun eşleşmesi gereken kimliği veya rolü temsil eder ve hem bildirime dayalı hem de zorunlu güvenlik denetimleri ile uyumludur. Ayrıca, bir sorumlu kimlik bilgilerine doğrudan erişebilir ve gerektiğinde kodunuzda rol ve kimlik denetimleri gerçekleştirebilirsiniz.  
  
 .NET Framework, esnek ve geniş bir uygulama yelpazesini karşılamak için yeterince Genişletilebilir rol tabanlı güvenlik desteği sağlar. COM+ 1,0 hizmetleri gibi mevcut kimlik doğrulama altyapılarla birlikte çalışabilme veya özel bir kimlik doğrulama sistemi oluşturma seçeneğini belirleyebilirsiniz. Rol tabanlı güvenlik, özellikle sunucuda işlenen ASP.NET Web uygulamalarında kullanım için uygun bir seçenektir. Ancak, istemci veya sunucu üzerinde rol tabanlı güvenlik .NET Framework kullanılabilir.  
  
 Bu bölümü okumadan önce, [anahtar güvenlik kavramları](../../../docs/standard/security/key-security-concepts.md)bölümünde sunulan malzemeleri anladığınızdan emin olun.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Sorumlu ve Kimlik Nesneleri](../../../docs/standard/security/principal-and-identity-objects.md)|Hem Windows hem de genel kimliklerin ve sorumluların nasıl ayarlanacağını ve yönetileceğini açıklar.|  
|[Temel Güvenlik Kavramları](../../../docs/standard/security/key-security-concepts.md)|.NET Framework güvenliği kullanmadan önce anlamanız gereken temel kavramları tanıtır.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
