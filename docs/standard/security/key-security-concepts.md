---
title: "Temel Güvenlik Kavramları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET Framework]
- security [.NET Framework], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e29b3c12fe89861574741506cb7cd018eb81b1d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="key-security-concepts"></a>Temel Güvenlik Kavramları
Rol tabanlı güvenlik güvenlik endişelere mobil kod hakkında Yardım için Microsoft .NET Framework sunar ve yapmak için kullanıcıların ne olduğunu belirlemek için bileşenlerini etkinleştiren desteği sağlamak için yetkili.  
  
## <a name="type-safety-and-security"></a>Tür güvenliği ve güvenlik  
 Tür kullanımı uyumlu kod erişimi için yetkilendirilmiş bellek konumlarını erişir. (Bu tartışma için tür güvenliği özellikle bellek tür güvenliği başvuruyor ve tür güvenliği daha geniş bir açısından ile karıştırılmamalıdır.) Örneğin, tür kullanımı uyumlu kod başka bir nesnenin özel alanlardan değerleri okunamıyor. Bu, yalnızca iyi tanımlanmış, izin verilen şekillerde türleri erişir.  
  
 Tam zamanında (JIT) derleme sırasında isteğe bağlı doğrulama işlemi, yerel makine türü güvenli olduklarını doğrulamak için kod içine JIT derlenmiş olması için bir yöntem, Microsoft Ara dili (MSIL) ve meta veri inceler. Kodu doğrulama atlama izni varsa bu işlemi atlandı. Doğrulama hakkında daha fazla bilgi için bkz: [yönetilen yürütme işlemi](../../../docs/standard/managed-execution-process.md).  
  
 Tür güvenliği doğrulanması yönetilen kodu çalıştırmak için zorunlu olmasa da, tür güvenliği derleme yalıtım ve güvenlik zorlama önemli bir rol oynar. Kod türü güvenli olduğunda, ortak dil çalışma zamanı derlemeleri birbirinden tamamen ayırabilirsiniz. Bu yalıtım derlemeleri birbirine olumsuz olamaz ve uygulamanın güvenilirliğini artırır sağlamaya yardımcı olur. Farklı düzeylerde güvenilen olsalar bile, tür kullanımı uyumlu bileşenleri aynı işlem içinde güvenle çalıştırabilirsiniz. Kod türü güvenli değil, istenmeyen yan etkileri ortaya çıkabilir. Örneğin, çalışma zamanı (yönetilmeyen) yerel kod içine çağırmak ve kötü amaçlı işlemlerini gerçekleştirme yönetilen kod engelleyemez. Kod türü güvenli olduğunda, bunu yapmak için izne sahip olmadığı sürece, yerel kod erişmez zamanının güvenlik zorlama mekanizması sağlar. Tür güvenli değil tüm kod verilmiş olmalıdır <xref:System.Security.Permissions.SecurityPermission> geçirilen enum üyeyle <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> çalıştırmak için.  
  
 Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Asıl  
 Sorumlu Kimliği ve kullanıcı rolü temsil eder ve kullanıcı adına hareket eder. .NET Framework'teki rol tabanlı güvenlik sorumluları üç tür destekler:  
  
-   Genel ilkeleri, kullanıcılar ve Windows kullanıcıları ve rolleri bağımsız mevcut rolleri temsil eder.  
  
-   Windows sorumluları Windows kullanıcıları ve kendi rolleri (veya kendi Windows grupları) temsil eder. Bir Windows asıl kimlik sunmak için kullanıcının bağlı olduğu sırada asıl kullanıcı adına bir kaynakta erişebilecektir başka bir kullanıcının kimliğine bürünebilir.  
  
-   Özel ilkeleri, belirli bir uygulama için gerekli herhangi bir şekilde bir uygulama tarafından tanımlanabilir. Bunlar sorumlusunun kimliğini ve rolleri temel kavramı genişletebilirsiniz.  
  
 Daha fazla bilgi için bkz: [asıl ve kimlik nesneleri](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Kimlik doğrulaması  
 Kimlik doğrulama bulmak ve kullanıcının kimlik bilgilerini inceleyerek ve bazı yetkilisi karşı bu kimlik bilgileri doğrulanıyor sorumlu kimliğini doğrulama işlemidir. Kimlik doğrulaması sırasında elde edilen bilgilerle kodunuz tarafından doğrudan kullanılabilir. .NET Framework rol tabanlı güvenlik, geçerli kullanıcının kimliğini doğrulamak ve kodunuzu erişmek bu asıl izin verilip verilmeyeceğini belirlemek için de kullanabilirsiniz. Aşırı bkz <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> örnekleri belirli roller sorumlusunun kimliğini doğrulamak yöntem. Örneğin, kullanabileceğiniz <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> aşırı geçerli kullanıcının Administrators grubunun üyesi olup olmadığını belirler.  
  
 Kimlik doğrulama mekanizmaları çeşitli bugün kullanılıyorsa, birçok .NET Framework rol tabanlı güvenliği ile kullanılabilir. En yaygın kullanılan mekanizmaları bazıları temel, Özet, Passport, işletim sistemi (örneğin, NTLM veya Kerberos) veya uygulama tanımlı mekanizmaları.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, etkin sorumlunun yönetici olmasını gerektirir. `name` Parametresi `null`, isteğe bağlı geçirmek için bir yönetici olan herhangi bir kullanıcı izin verir.  
  
> [!NOTE]
>  Windows Vista'da, kullanıcı ayrıcalıkları kullanıcı hesabı denetimi (UAC) belirler. Yerleşik Yöneticiler grubunun bir üyesi iseniz, size iki çalışma zamanı erişim belirteci atanır: Standart kullanıcı erişim belirteci ve yönetici erişim belirteci. Varsayılan olarak, standart kullanıcı rolünde olursunuz. Bir yönetici olmanız gerekir kod yürütmek için önce ayrıcalıklarınız standart kullanıcıdan yöneticisine Yükselt gerekir. Uygulama simgesi sağ tıklayarak ve yönetici olarak çalıştırmak istediğiniz belirten bir uygulama başlattığınızda bunu yapabilirsiniz.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 Aşağıdaki örnek, asıl ve asıl kullanılabilir rolleri kimliğini belirlemek gösterilmiştir. Geçerli kullanıcının bir rol, uygulamanızın kullanmak için izin olduğunu onaylamak için bu örnek bir uygulama olabilir.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Yetkilendirme  
 Yetkilendirme istenen eylemi gerçekleştirmek için sorumlu izin verilip verilmediğini belirleme işlemidir. Yetkilendirme kimlik doğrulamasından sonra gerçekleşir ve sorumlusunun kimliğini ve rolleri hakkında bilgi sorumluya erişmek hangi kaynakların belirlemek için kullanır. .NET Framework rol tabanlı güvenlik, kimlik doğrulaması uygulamak için kullanabilirsiniz.
