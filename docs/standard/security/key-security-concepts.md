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
ms.openlocfilehash: b7bcb7e56ca14d129eadcaeac19452d4a443713d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400661"
---
# <a name="key-security-concepts"></a>Temel Güvenlik Kavramları
Microsoft .NET Framework, mobil kodla ilgili güvenlik endişelerini gidermeye yardımcı olmak ve bileşenlerin kullanıcıların ne yapmaya yetkili olduğunu belirlemesine olanak tanıyan destek sağlamak için rol tabanlı güvenlik sunar.  
  
## <a name="type-safety-and-security"></a>Tip güvenliği ve emniyet  
 Tür güvenli kod, yalnızca erişmeye yetkili olduğu bellek konumlarına erişir. (Bu tartışma için, tür güvenliği özellikle bellek türü güvenliği anlamına gelir ve daha geniş bir açıdan tür güvenliği ile karıştırılmamalıdır.) Örneğin, tür güvenli kod başka bir nesnenin özel alanlarından değerleri okuyamaz. Türlere yalnızca iyi tanımlanmış, izin verilebilen yollarla erişir.  
  
 Tam zamanında (JIT) derleme sırasında, isteğe bağlı bir doğrulama işlemi, tür güvenli olduklarını doğrulamak için jit tarafından derlenecek bir yöntemin meta verilerini ve Microsoft ara dilini (MSIL) inceler. Kodun doğrulamayı atlama izni varsa bu işlem atlanır. Doğrulama hakkında daha fazla bilgi için Yönetilen [Yürütme Süreci'ne](../../../docs/standard/managed-execution-process.md)bakın.  
  
 Yönetilen kodu çalıştırmak için tür güvenliğinin doğrulanması zorunlu olmasa da, tür güvenliği montaj yalıtımı ve güvenlik zorlamada önemli bir rol oynar. Kod güvenli bir tür olduğunda, ortak dil çalışma zamanı derlemeleri birbirinden tamamen yalıtabilir. Bu yalıtım, derlemelerin birbirini olumsuz etkilememesini sağlamaya yardımcı olur ve uygulama güvenilirliğini artırır. Tür-güvenli bileşenler, farklı düzeylerde güvenilen olsalar bile aynı işlemde güvenli bir şekilde çalıştırılabilir. Kod güvenli bir şekilde yazılmamışsa, istenmeyen yan etkiler oluşabilir. Örneğin, çalışma zamanı yönetilen kodun yerel (yönetilmeyen) koda çağrılmasını ve kötü amaçlı işlemler gerçekleştirmesini engelleyemez. Kod güvenli olduğunda, çalışma zamanının güvenlik zorlama mekanizması, izin verilmedikçe yerel koda erişmemesini sağlar. Güvenli olmayan tüm kod, çalıştırmak için <xref:System.Security.Permissions.SecurityPermission> geçen enum <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> üyesi ile verilmiş olmalıdır.  
  
 Daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](../../../docs/framework/misc/code-access-security-basics.md)bakın.  
  
## <a name="principal"></a>Asıl  
 Bir asıl, kullanıcının kimliğini ve rolünü temsil eder ve kullanıcı adına hareket eder. .NET Framework'deki rol tabanlı güvenlik üç tür temeli destekler:  
  
- Genel ilkeler, Windows kullanıcıları ve rollerinden bağımsız olarak var olan kullanıcıları ve rolleri temsil eder.  
  
- Windows ilkeleri, Windows kullanıcılarını ve rollerini (veya Windows gruplarını) temsil eder. Windows ilkesi başka bir kullanıcının kimliğine bürünebilir, bu da ana bilgisayarın o kullanıcıya ait kimliği sunarken bir kaynağa kullanıcı adına erişebileceği anlamına gelir.  
  
- Özel ilkeler, bir uygulama tarafından, o uygulama için gerekli olan herhangi bir şekilde tanımlanabilir. Müdürün kimliği ve rolleri hakkında temel kavramları genişletebilirler.  
  
 Daha fazla bilgi için [Bkz. Asıl ve Kimlik Nesneleri.](../../../docs/standard/security/principal-and-identity-objects.md)  
  
## <a name="authentication"></a>Kimlik Doğrulaması  
 Kimlik doğrulaması, kullanıcının kimlik bilgilerini inceleyerek ve bu kimlik bilgilerini bazı yetkilere karşı doğrulayarak bir müdürün kimliğini bulma ve doğrulama işlemidir. Kimlik doğrulama sırasında elde edilen bilgiler doğrudan kodunuz tarafından kullanılabilir. Geçerli kullanıcının kimliğini doğrulamak ve bu müdürün kodunuza erişmesine izin verip vermeyeceğinizi belirlemek için .NET Framework rol tabanlı güvenliği de kullanabilirsiniz. Belirli roller için <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> asılın nasıl doğrulaşdırılabildiğini örnekler için yöntemin aşırı yüklerine bakın. Örneğin, geçerli kullanıcının <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> Yöneticiler grubunun bir üyesi olup olmadığını belirlemek için aşırı yüklemeyi kullanabilirsiniz.  
  
 Günümüzde birçoğu .NET Framework rol tabanlı güvenlik ile kullanılabilen çeşitli kimlik doğrulama mekanizmaları kullanılmaktadır. En sık kullanılan mekanizmalardan bazıları temel, özet, Pasaport, işletim sistemi (NTLM veya Kerberos gibi) veya uygulama tanımlı mekanizmalardır.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, etkin müdürün yönetici olmasını gerektirir. `name` Parametre, yönetici olan herhangi bir kullanıcının talebi geçirmesini `null`sağlar.  
  
> [!NOTE]
> Windows Vista'da, Kullanıcı Hesabı Denetimi (UAC) bir kullanıcının ayrıcalıklarını belirler. Yerleşik Yöneticiler grubunun bir üyesi iseniz, size iki çalışma zamanı erişim belirteci atanır: Standart kullanıcı erişim belirteci ve yönetici erişim belirteci. Varsayılan olarak, standart kullanıcı rolünde olursunuz. Yönetici olmanızı gerektiren kodu yürütmek için öncelikle ayrıcalıklarınızı standart kullanıcıdan yöneticiye yükseltmeniz gerekir. Bunu, uygulama simgesine sağ tıklayarak ve yönetici olarak çalıştırmak istediğinizi belirterek bir uygulamayı başlattığınızda yapabilirsiniz.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 Aşağıdaki örnek, asılın kimliğinin ve asılların kullanabileceği rollerin nasıl belirlenip belirlendirilebildiğini gösterir. Bu örneğin bir uygulaması, geçerli kullanıcının uygulamanızı kullanmak için izin verdiğiniz bir rolde olduğunu onaylamak için olabilir.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Yetkilendirme  
 Yetkilendirme, bir asıl'un istenen bir eylemi gerçekleştirmesine izin verilip verilmediğini belirleme işlemidir. Yetkilendirme kimlik doğrulamadan sonra gerçekleşir ve müdürün hangi kaynaklara erişebileceğini belirlemek için müdürün kimliği ve rolleri hakkındaki bilgileri kullanır. Yetkilendirmeyi uygulamak için .NET Framework rol tabanlı güvenliği kullanabilirsiniz.
