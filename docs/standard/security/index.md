---
title: .NET içinde güvenlik
ms.date: 06/04/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, security
- security [.NET], about security
- application development [.NET], security
- security [.NET Framework]
- security [.NET]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e60f463d5a691cb84a30c169e471aa905b2db17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61860561"
---
# <a name="security-in-net"></a><span data-ttu-id="2b06c-102">.NET içinde güvenlik</span><span class="sxs-lookup"><span data-stu-id="2b06c-102">Security in .NET</span></span>
<span data-ttu-id="2b06c-103">Ortak dil çalışma zamanı ve .NET birçok yararlı sınıfları ve sistem yöneticileri için kod erişebilmesi için izinleri özelleştirmek kolayca güvenli kod yazma ve geliştiricilerin Hizmetleri korunan kaynakları sağlayın.</span><span class="sxs-lookup"><span data-stu-id="2b06c-103">The common language runtime and the .NET provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="2b06c-104">Ayrıca, çalışma zamanı ve .NET yararlı sınıfları ve şifreleme ve rol tabanlı güvenlik kullanımını kolaylaştıran hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b06c-104">In addition, the runtime and the .NET provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2b06c-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2b06c-105">In This Section</span></span>  

 [<span data-ttu-id="2b06c-106">Temel Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="2b06c-106">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="2b06c-107">Bir genel bakış ortak dil çalışma zamanı güvenlik özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b06c-107">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="2b06c-108">Bu bölümde geliştiriciler ve sistem yöneticileri ilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="2b06c-108">This section is of interest to developers and system administrators.</span></span>  
  
 [<span data-ttu-id="2b06c-109">Rol Tabanlı Güvenlik</span><span class="sxs-lookup"><span data-stu-id="2b06c-109">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)  
 <span data-ttu-id="2b06c-110">Rol tabanlı güvenlik, kodunuzda etkileşim açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b06c-110">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="2b06c-111">Bu bölümde geliştiricileri ilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="2b06c-111">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="2b06c-112">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="2b06c-112">Cryptography Model</span></span>](../../../docs/standard/security/cryptography-model.md)  
 <span data-ttu-id="2b06c-113">.NET tarafından sağlanan şifreleme hizmetlerine genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b06c-113">Provides an overview of cryptographic services provided by .NET.</span></span> <span data-ttu-id="2b06c-114">Bu bölümde geliştiricileri ilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="2b06c-114">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="2b06c-115">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2b06c-115">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="2b06c-116">Güvenilir .NET uygulamaları oluşturmak için en iyi uygulamalardan bazılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b06c-116">Describes some of the best practices for creating reliable .NET applications.</span></span> <span data-ttu-id="2b06c-117">Bu bölümde geliştiricileri ilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="2b06c-117">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="2b06c-118">Yönetilmeyen Kod İçin Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2b06c-118">Secure Coding Guidelines for Unmanaged Code</span></span>](../../../docs/framework/security/secure-coding-guidelines-for-unmanaged-code.md)  
 <span data-ttu-id="2b06c-119">Bazı en iyi uygulamaları ve güvenlikle ilgili noktalar, yönetilmeyen kod çağırırken açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b06c-119">Describes some of the best practices and security concerns when calling unmanaged code.</span></span>  
  
 [<span data-ttu-id="2b06c-120">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="2b06c-120">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)  
 <span data-ttu-id="2b06c-121">Uygulamalarınızda beyana dayalı kimlik nasıl uygulayacağınıza dair açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b06c-121">Describes how you can implement claims-based identity in your applications.</span></span>  

<span data-ttu-id="2b06c-122">[Güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md) .NET Framework güvenlik sistemini önemli değişiklikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b06c-122">[Security Changes](../../../docs/framework/security/security-changes.md) Describes important changes to the .NET Framework security system.</span></span>

## <a name="related-sections"></a><span data-ttu-id="2b06c-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2b06c-123">Related Sections</span></span>  
 [<span data-ttu-id="2b06c-124">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2b06c-124">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="2b06c-125">Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b06c-125">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
