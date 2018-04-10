---
title: .NET Framework'te Güvenlik
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .NET Framework, security
- security [.NET Framework], about security
- application development [.NET Framework], security
- security [.NET Framework]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
caps.latest.revision: 37
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7f8600da624ff75ce2dbd5c417f886d6b3b1ac37
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="security-in-the-net-framework"></a><span data-ttu-id="ff0c3-102">.NET Framework'te Güvenlik</span><span class="sxs-lookup"><span data-stu-id="ff0c3-102">Security in the .NET Framework</span></span>
<span data-ttu-id="ff0c3-103">Ortak dil çalışma zamanı ve .NET Framework pek çok yararlı sınıfları sağlar ve kolayca güvenli kod yazma ve sistem yöneticileri, erişebilmesi için kodu izinler özelleştirmek etkinleştirmek, geliştiricilerin Hizmetleri korunan kaynakları.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-103">The common language runtime and the .NET Framework provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="ff0c3-104">Ayrıca, çalışma zamanı ve .NET Framework yararlı sınıfları ve şifreleme ve rol tabanlı güvenlik kullanımını kolaylaştırmak hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-104">In addition, the runtime and the .NET Framework provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff0c3-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ff0c3-105">In This Section</span></span>  
 [<span data-ttu-id="ff0c3-106">Güvenlik Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="ff0c3-106">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)  
 <span data-ttu-id="ff0c3-107">.NET Framework güvenlik sistemi önemli değişiklikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-107">Describes important changes to the .NET Framework security system.</span></span>  
  
 [<span data-ttu-id="ff0c3-108">Temel Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="ff0c3-108">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="ff0c3-109">Bir genel bakış ortak dil çalışma zamanı güvenlik özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-109">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="ff0c3-110">Bu bölümde geliştiriciler ve sistem yöneticileri için ilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-110">This section is of interest to developers and system administrators.</span></span>  
  
 [<span data-ttu-id="ff0c3-111">Rol Tabanlı Güvenlik</span><span class="sxs-lookup"><span data-stu-id="ff0c3-111">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)  
 <span data-ttu-id="ff0c3-112">Rol tabanlı güvenlik, kodunuzda etkileşimde açıklar.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-112">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="ff0c3-113">Bu bölümde geliştiricilere ilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-113">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="ff0c3-114">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="ff0c3-114">Cryptography Model</span></span>](../../../docs/standard/security/cryptography-model.md)  
 <span data-ttu-id="ff0c3-115">.NET Framework tarafından sağlanan şifreleme hizmetlerine genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-115">Provides an overview of cryptographic services provided by the .NET Framework.</span></span> <span data-ttu-id="ff0c3-116">Bu bölümde geliştiricilere ilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-116">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="ff0c3-117">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ff0c3-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="ff0c3-118">Bazı güvenilir .NET Framework uygulamaları oluşturmak için en iyi uygulamaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-118">Describes some of the best practices for creating reliable .NET Framework applications.</span></span> <span data-ttu-id="ff0c3-119">Bu bölümde geliştiricilere ilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-119">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="ff0c3-120">Yönetilmeyen Kod İçin Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ff0c3-120">Secure Coding Guidelines for Unmanaged Code</span></span>](../../../docs/framework/security/secure-coding-guidelines-for-unmanaged-code.md)  
 <span data-ttu-id="ff0c3-121">En iyi uygulamaları ve güvenlikle ilgili sorunların bazıları, yönetilmeyen kod çağrılırken açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-121">Describes some of the best practices and security concerns when calling unmanaged code.</span></span>  
  
 [<span data-ttu-id="ff0c3-122">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="ff0c3-122">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)  
 <span data-ttu-id="ff0c3-123">Uygulamalarınızda talep tabanlı kimlik nasıl uygulayacağınıza dair açıklar.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-123">Describes how you can implement claims-based identity in your applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ff0c3-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ff0c3-124">Related Sections</span></span>  
 [<span data-ttu-id="ff0c3-125">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ff0c3-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="ff0c3-126">Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff0c3-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
