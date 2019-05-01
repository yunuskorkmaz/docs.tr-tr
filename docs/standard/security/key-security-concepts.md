---
title: Temel Güvenlik Kavramları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET Framework]
- security [.NET Framework], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c483baeca9efcbc4a38020a7b2f4fa221a6b4028
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018625"
---
# <a name="key-security-concepts"></a>Temel Güvenlik Kavramları
Microsoft .NET Framework mobil kod ile ilgili güvenlik endişelerini adresi yardımcı olmak için rol tabanlı güvenlik sunar ve yapmak için yetkili kullanıcıların ne belirlemek bileşenler sağlayan destek sağlar.  
  
## <a name="type-safety-and-security"></a>Tür güvenliği ve emniyeti  
 Tür kullanımı uyumlu kod yalnızca erişmek için yetkili bellek konumlarına erişir. (Bu tartışma için tür güvenliği özellikle bellek türü güvenliğine başvurur ve daha geniş bir açısından tür güvenliği ile karıştırılmamalıdır.) Örneğin, tür kullanımı uyumlu kod başka nesnenin özel alanlarındaki değerleri okuyamıyor. Bu türler yalnızca iyi tanımlanmış, izin verilen şekilde erişir.  
  
 Just-ın-time (JIT) derleme sırasında isteğe bağlı doğrulama işlemi, yerel makine tür güvenli olduklarını doğrulamak için kod içine JIT olarak derlenmiş olması, bir yöntemin meta verileri ve Microsoft Ara dilini (MSIL) inceler. Bu işlem, kod doğrulamayı atlama izni varsa atlanır. Doğrulama hakkında daha fazla bilgi için bkz: [Managed Execution Process](../../../docs/standard/managed-execution-process.md).  
  
 Tür güvenliği doğrulamasının yönetilen kodu çalıştırma zorunlu olmasa da, tür güvenliği derleme yalıtımında ve güvenlik zorlamada çok önemli bir rol oynar. Kod tür bakımından güvenli olduğunda, ortak dil çalışma zamanı derlemeleri birbirinden tamamen ayırabilirsiniz. Bu yalıtım, derlemelerin birbirini olumsuz olamaz ve uygulama güvenilirliği artırır emin olun yardımcı olur. Farklı düzeylerde güvenilir olsalar bile, tür açısından güvenli bileşenler aynı işlem içinde güvenli bir şekilde yürütebilirsiniz. Kod tür bakımından güvenli olmadığında, istenmeyen yan etkiler oluşabilir. Örneğin, çalışma zamanı yönetilen kodun yerel (yönetilmeyen) koda çağrılmasını ve kötü amaçlı işlemler gerçekleştirmesini önleyemez. Kod tür bakımından güvenli olduğunda, bunu yapmak için izne sahip olmadığı sürece, yerel kod erişmez çalışma zamanı güvenlik zorlama mekanizması sağlar. Tür bakımından güvenli değil tüm kodun vermiş olması gerekir <xref:System.Security.Permissions.SecurityPermission> geçirilen numaralandırma üyesi ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> çalıştırılacak.  
  
 Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Asıl  
 Sorumlu Kimliği ve kullanıcı rolünü temsil eden ve kullanıcı adına hareket eder. .NET Framework'teki rol tabanlı güvenlik sorumluları üç tür destekler:  
  
- Genel ilkeleri, kullanıcılar ve Windows kullanıcıları ve rolleri, bağımsız kayıtlı rolleri temsil eder.  
  
- Windows sorumluları Windows kullanıcıları ve rolleri (veya kendi Windows grupları) temsil eder. Bir Windows asıl sorumlusu, kimlik sunmak için kullanıcının bağlı olduğu sırada bir kullanıcı adına bir kaynakta erişebileceği anlamına gelir başka bir kullanıcının kimliğine bürünebilirsiniz.  
  
- Özel ilkeleri, belirli bir uygulama için gerekli herhangi bir şekilde bir uygulama tarafından tanımlanabilir. Bunlar, sorumlunun kimliğini ve rolleri temel kavramı genişletebilirsiniz.  
  
 Daha fazla bilgi için [asıl ve kimlik nesneleri](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Kimlik doğrulaması  
 Kimlik doğrulaması bulma ve kullanıcının kimlik bilgilerini inceleyerek ve bu kimlik bilgilerini bir yetkili karşı doğrulama sorumlu kimliğini doğrulama işlemidir. Kimlik doğrulaması sırasında elde edilen bilgilerin kodunuz tarafından doğrudan kullanılabilir. .NET Framework rol tabanlı güvenlik, geçerli kullanıcının kimliğini doğrulamak ve kodunuzu erişmek bu sorumlusunun izin verilip verilmeyeceğini belirlemek için de kullanabilirsiniz. Aşırı yüklemeleri bkz <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> belirli rolleri için asıl kimlik doğrulaması yapmayı örnekleri için yöntemi. Örneğin, kullanabileceğiniz <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> geçerli kullanıcının Administrators grubunun üyesi olup olmadığını belirlemek için aşırı yükleme.  
  
 Kimlik doğrulama mekanizmaları çeşitli bugün kullanılıyorsa, çoğu .NET Framework rol tabanlı güvenlik ile kullanılabilir. En sık kullanılan mekanizma bazı temel, Özet, Passport, (örneğin, NTLM veya Kerberos) işletim sistemi veya uygulama tanımlı mekanizmaları.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, etkin sorumlunun yönetici olmasını gerektirir. `name` Parametresi `null`, bir yönetici talebi geçirilecek herhangi bir kullanıcı sağlar.  
  
> [!NOTE]
>  Windows Vista'da, kullanıcı hesabı denetimi (UAC) bir kullanıcının ayrıcalıkları belirler. Yerleşik Yöneticiler grubunun bir üyesi iseniz, size iki çalışma zamanı erişim belirteci atanır: Standart kullanıcı erişim belirteci ve yönetici erişim belirteci. Varsayılan olarak, standart kullanıcı rolünde olursunuz. Yönetici olmasını gerektiren kodları yürütmek için öncelikle, standart kullanıcıdan yöneticiye ayrıcalıklarını gerekir. Uygulama simgesine tıklayıp yönetici olarak çalıştırmak istediğiniz belirten bir uygulamayı başlattığınızda bunu yapabilirsiniz.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 Aşağıdaki örnek, asıl ve sorumlusuna kullanılabilir rolleri kimliğini belirlemek nasıl gösterir. Geçerli kullanıcının uygulamanızı kullanmak için izin rol olduğunu onaylamak için bu örnek, bir uygulama olabilir.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Yetkilendirme  
 Yetkilendirme, bir sorumlunun istenen eylemi gerçekleştirmek için izin verilip verilmeyeceğini belirleme işlemidir. Yetkilendirme kimlik doğrulamasından sonra gerçekleşir ve sorumlusunun kimlik ve rolleri hakkında bilgi sorumluya erişmek hangi kaynakları belirlemek için kullanır. .NET Framework rol tabanlı güvenlik, kimlik doğrulaması uygulamak için kullanabilirsiniz.
