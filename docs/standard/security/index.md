---
title: .NET içinde güvenlik
description: .NET ' te güvenlik hakkında bilgi edinin. Anahtar güvenlik kavramlarını, rol tabanlı güvenliği, şifreleme modelini ve güvenli kodlama kılavuzlarını tanımlayan bağlantıları izleyin.
ms.date: 06/04/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, security
- security [.NET], about security
- application development [.NET], security
- security [.NET Framework]
- security [.NET]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
ms.openlocfilehash: 21511b580a4f922d2aef04cc79f5d551f0406b45
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767825"
---
# <a name="security-in-net"></a><span data-ttu-id="9bd19-104">.NET içinde güvenlik</span><span class="sxs-lookup"><span data-stu-id="9bd19-104">Security in .NET</span></span>

<span data-ttu-id="9bd19-105">Ortak dil çalışma zamanı ve .NET, geliştiricilerin güvenli kodu kolayca yazmasını ve sistem yöneticilerinin, korunan kaynaklara erişebilmesi için koda verilen izinleri özelleştirmesini sağlayan birçok yararlı sınıf ve hizmeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bd19-105">The common language runtime and the .NET provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="9bd19-106">Ayrıca, çalışma zamanı ve .NET, şifreleme ve rol tabanlı güvenlik kullanımını kolaylaştıran yararlı sınıflar ve hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bd19-106">In addition, the runtime and the .NET provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9bd19-107">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="9bd19-107">In this section</span></span>

- [<span data-ttu-id="9bd19-108">Temel Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="9bd19-108">Key Security Concepts</span></span>](key-security-concepts.md)  
<span data-ttu-id="9bd19-109">Ortak dil çalışma zamanı güvenlik özelliklerine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bd19-109">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="9bd19-110">Bu bölüm, geliştiricilere ve sistem yöneticilerine yönelik bir ilgi alanıdır.</span><span class="sxs-lookup"><span data-stu-id="9bd19-110">This section is of interest to developers and system administrators.</span></span>

- [<span data-ttu-id="9bd19-111">Rol tabanlı güvenlik</span><span class="sxs-lookup"><span data-stu-id="9bd19-111">Role-Based Security</span></span>](role-based-security.md)  
<span data-ttu-id="9bd19-112">Kodunuzda rol tabanlı güvenlikle nasıl etkileşim kuracağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="9bd19-112">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="9bd19-113">Bu bölüm, geliştiricilere ilgi çekici.</span><span class="sxs-lookup"><span data-stu-id="9bd19-113">This section is of interest to developers.</span></span>

- [<span data-ttu-id="9bd19-114">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="9bd19-114">Cryptography Model</span></span>](cryptography-model.md)  
<span data-ttu-id="9bd19-115">.NET tarafından sağlanan şifreleme hizmetlerine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bd19-115">Provides an overview of cryptographic services provided by .NET.</span></span> <span data-ttu-id="9bd19-116">Bu bölüm, geliştiricilere ilgi çekici.</span><span class="sxs-lookup"><span data-stu-id="9bd19-116">This section is of interest to developers.</span></span>

- [<span data-ttu-id="9bd19-117">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9bd19-117">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)  
<span data-ttu-id="9bd19-118">Güvenilir .NET uygulamaları oluşturmak için en iyi uygulamalardan bazılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9bd19-118">Describes some of the best practices for creating reliable .NET applications.</span></span> <span data-ttu-id="9bd19-119">Bu bölüm, geliştiricilere ilgi çekici.</span><span class="sxs-lookup"><span data-stu-id="9bd19-119">This section is of interest to developers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="9bd19-120">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="9bd19-120">Related sections</span></span>

[<span data-ttu-id="9bd19-121">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9bd19-121">Development Guide</span></span>](../../framework/development-guide.md)  
<span data-ttu-id="9bd19-122">Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bd19-122">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
