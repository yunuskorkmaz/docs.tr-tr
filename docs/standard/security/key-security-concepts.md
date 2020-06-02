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
ms.openlocfilehash: 1ec811430056b7db575d6db229a3afe618850e49
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291246"
---
# <a name="key-security-concepts"></a>Temel Güvenlik Kavramları
Microsoft .NET Framework, mobil kodla ilgili güvenlik kaygılarını ele almak ve bileşenlerin hangi kullanıcılara izin verildiğini belirlemesini sağlayan destek sağlamak için rol tabanlı güvenlik sunar.  
  
## <a name="type-safety-and-security"></a>Tür güvenliği ve güvenlik  
 Tür kullanımı uyumlu kod yalnızca erişim yetkisi olan bellek konumlarına erişir. (Bu tartışma için, tür güvenliği özellikle bellek türü güvenliğine başvurur ve tür güvenliği daha geniş bir bakımdan karıştırılmamalıdır.) Örneğin, tür kullanımı uyumlu kod başka bir nesnenin özel alanlarından değerleri okuyamıyor. Yalnızca iyi tanımlanmış, izin verilen yöntemlerle türlere erişir.  
  
 Tam zamanında (JıT) derleme sırasında, isteğe bağlı bir doğrulama işlemi, güvenli türde olduklarını doğrulamak için yerel makine koduna JıT olarak derlenmek üzere bir yöntemin meta verilerini ve Microsoft ara dili 'ni (MSIL) inceler. Bu işlem, kodun doğrulamayı atlama izni varsa atlanır. Doğrulama hakkında daha fazla bilgi için bkz. [yönetilen yürütme işlemi](../managed-execution-process.md).  
  
 Tür güvenliği doğrulaması yönetilen kodu çalıştırmak için zorunlu olmasa da, tür güvenliği derleme yalıtımı ve güvenlik zorlaması için önemli bir rol oynar. Kod tür güvenolduğunda, ortak dil çalışma zamanı derlemeleri tamamen tamamen yalıtabilir. Bu yalıtım, derlemelerin birbirini olumsuz şekilde etkilememesini sağlar ve uygulama güvenilirliğini artırır. Tür açısından güvenli bileşenler, farklı düzeylerde güvenilir olsalar bile aynı işlemde güvenli bir şekilde çalıştırılabilir. Kod türü güvenli olmadığında istenmeyen yan etkiler meydana gelebilir. Örneğin, çalışma zamanı yönetilen kodun yerel (yönetilmeyen) koda çağrılmasını ve kötü amaçlı işlemler gerçekleştirmesini engellemez. Kod türü güvenli olduğunda, çalışma zamanının güvenlik zorlama mekanizması, bunu yapmak için izne sahip olmadığı müddetçe yerel koda erişemez. Türü güvenli olmayan tüm kodlar <xref:System.Security.Permissions.SecurityPermission> , geçirilen enum üyesine <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> çalıştırılacak şekilde verilmiş olmalıdır.  
  
 Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Asıl  
 Bir sorumlu bir kullanıcının kimliğini ve rolünü temsil eder ve kullanıcının adına davranır. .NET Framework rol tabanlı güvenlik, üç tür sorumlusu destekler:  
  
- Genel sorumlular, Windows kullanıcıları ve rollerinden bağımsız olarak bulunan kullanıcıları ve rolleri temsil eder.  
  
- Windows sorumluları Windows kullanıcılarını ve rollerini (veya Windows gruplarını) temsil eder. Bir Windows sorumlusu başka bir kullanıcının kimliğine bürünerek, sorumlu bu kullanıcıya ait olan kimliği sunarken kullanıcının adına bir kaynağa erişebileceği anlamına gelir.  
  
- Özel sorumlular, belirli bir uygulama için gerekli olan herhangi bir şekilde bir uygulama tarafından tanımlanabilir. Bu kişiler, sorumlu kimlik ve rollerinin temel kavramının kapsamını genişletebilirler.  
  
 Daha fazla bilgi için bkz. [Principal ve Identity Objects](principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Kimlik Doğrulaması  
 Kimlik doğrulaması, kullanıcının kimlik bilgilerini inceleyerek ve bu kimlik bilgilerini bazı yetkililerle doğrulayarak sorumlu kimliğini bulma ve doğrulama işlemidir. Kimlik doğrulama sırasında elde edilen bilgiler, kodunuz tarafından doğrudan kullanılabilir. Ayrıca, geçerli kullanıcının kimliğini doğrulamak ve bu sorumlunun kodunuza erişmesine izin verip vermeyeceğinizi anlamak için rol tabanlı güvenlik .NET Framework de kullanabilirsiniz. <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType>Belirli roller için sorumlunun nasıl doğrulanacağını gösteren örnekler için, yönteminin aşırı yüklerini inceleyin. Örneğin, <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> geçerli kullanıcının Yöneticiler grubunun bir üyesi olup olmadığını anlamak için aşırı yüklemeyi kullanabilirsiniz.  
  
 Günümüzde çok çeşitli kimlik doğrulama mekanizmaları kullanılır ve rol tabanlı güvenlik .NET Framework kullanılabilir. En yaygın olarak kullanılan mekanizmalardan bazıları temel, Özet, Passport, işletim sistemi (NTLM veya Kerberos gibi) veya uygulama tanımlı mekanizmalarda oluşur.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, etkin sorumlunun yönetici olmasını gerektirir. `name`Parametresi `null` , yönetici olan herhangi bir kullanıcının talebi geçmesine izin verir.  
  
> [!NOTE]
> Windows Vista 'da, Kullanıcı hesabı denetimi (UAC) bir kullanıcının ayrıcalıklarını belirler. Yerleşik Yöneticiler grubunun bir üyesi iseniz, size iki çalışma zamanı erişim belirteci atanır: Standart kullanıcı erişim belirteci ve yönetici erişim belirteci. Varsayılan olarak, standart kullanıcı rolünde olursunuz. Yönetici olmanızı gerektiren kodu yürütmek için öncelikle standart Kullanıcı olan ayrıcalıklarınızı yöneticiye yükseltmeniz gerekir. Uygulamayı başlattığınızda uygulama simgesine sağ tıklayıp yönetici olarak çalıştırmak istediğinizi belirterek bunu yapabilirsiniz.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 Aşağıdaki örnek, sorumlunun kimliğinin ve asıl için kullanılabilen rollerin nasıl belirleneceğini göstermektedir. Bu örneğin bir uygulaması, geçerli kullanıcının uygulamanızı kullanmaya izin veren bir rolde olduğunu doğrulamak olabilir.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Yetkilendirme  
 Yetkilendirme, bir sorumlunun istenen eylemi gerçekleştirmesine izin verilip verilmeyeceğini belirleme işlemidir. Kimlik doğrulamasından sonra yetkilendirme oluşur ve sorumlunun erişebileceği kaynakları belirlemek için sorumlunun kimliği ve rolleri hakkında bilgi kullanır. Yetkilendirmeyi uygulamak için rol tabanlı güvenlik .NET Framework kullanabilirsiniz.
