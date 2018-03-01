---
title: .NET framework 4.7, 4.6 ve 4.5
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
f1_keywords:
- f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 34402e74bb0cb560d213760c38ce4b936d712eb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-guide"></a><span data-ttu-id="40014-102">.NET framework Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="40014-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="40014-103">Bu .NET Framework İçerik kümesi için .NET Framework sürüm 4.5 ve 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 ve 4.7.1 bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="40014-103">This .NET Framework content set includes information for .NET Framework versions 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, and 4.7.1.</span></span> <span data-ttu-id="40014-104">.NET Framework indirmek için bkz: [.NET Framework yükleme](../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="40014-104">To download the .NET Framework, see [Installing the .NET Framework](../../docs/framework/install/guide-for-developers.md).</span></span> <span data-ttu-id="40014-105">Yeni özellikler ve NET Framework 4.5, değişikliklerin bir listesi için [!INCLUDE[net_v46](../../includes/net-v46-md.md)], kendi noktası serbest bırakır ve .NET Framework 4.7 ve 4.7.1, bkz: [.NET Framework'teki yenilikler](../../docs/framework/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="40014-105">For a list of new features and changes in the NET Framework 4.5, the [!INCLUDE[net_v46](../../includes/net-v46-md.md)], their point releases, and the .NET Framework 4.7 and 4.7.1, see [What's New in the .NET Framework](../../docs/framework/whats-new/index.md).</span></span> <span data-ttu-id="40014-106">Desteklenen platformlar listesi için bkz: [.NET Framework sistem gereksinimleri](../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40014-106">For a list of supported platforms, see [.NET Framework System Requirements](../../docs/framework/get-started/system-requirements.md).</span></span> 

<span data-ttu-id="40014-107">.NET Framework, web, Windows, Windows Phone, Windows Server ve Microsoft Azure için uygulamaları oluşturmaya yönelik bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="40014-107">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="40014-108">Ortak dil çalışma zamanı (CLR) ve çok çeşitli işlevleri ve çoğu endüstri standartları için destek içerir .NET Framework sınıf kitaplığı oluşur.</span><span class="sxs-lookup"><span data-stu-id="40014-108">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="40014-109">.NET Framework'te bellek yönetimi, türü ve bellek güvenliği, güvenlik, ağ ve uygulama dağıtımı gibi birçok hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="40014-109">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="40014-110">Kullanımı kolay veri yapılarını ve alt düzey Windows işletim sistemi soyut API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="40014-110">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="40014-111">C#, F # ve Visual Basic dahil olan .NET Framework ile çeşitli programlama dillerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40014-111">You can use a variety of programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>  

<span data-ttu-id="40014-112">Kullanıcılar ve geliştiriciler için .NET Framework genel bir giriş için bkz: [Başlarken](../../docs/framework/get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="40014-112">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](../../docs/framework/get-started/index.md).</span></span> <span data-ttu-id="40014-113">Mimari ve .NET Framework'ün anahtar özellikler bir giriş için bkz: [genel bakış](../../docs/framework/get-started/overview.md).</span><span class="sxs-lookup"><span data-stu-id="40014-113">For an introduction to the architecture and key features of the .NET Framework, see the [overview](../../docs/framework/get-started/overview.md).</span></span>  

<span data-ttu-id="40014-114">.NET Framework ve Docker ile kullanılan [Windows kapsayıcıları](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).</span><span class="sxs-lookup"><span data-stu-id="40014-114">The .NET Framework can be used with Docker and with [Windows Containers](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).</span></span> <span data-ttu-id="40014-115">Bkz: [dağıtma .NET Framework uygulamaları docker'la](./docker/index.md) Docker kapsayıcılarında uygulamalarınızı çalıştırmak öğrenmek için.</span><span class="sxs-lookup"><span data-stu-id="40014-115">See [Deploying .NET Framework applications with Docker](./docker/index.md) to learn how to run your applications in Docker containers.</span></span>

## <a name="installation"></a><span data-ttu-id="40014-116">Yükleme</span><span class="sxs-lookup"><span data-stu-id="40014-116">Installation</span></span>

<span data-ttu-id="40014-117">.NET Framework, .NET Framework uygulamaları çalıştırmak etkinleştirme Windows ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="40014-117">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="40014-118">Windows sürümü ile birlikte gelen çok .NET Framework'ün sonraki bir sürümünü gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="40014-118">You may need a later version of the .NET Framework than comes with your Windows version.</span></span> <span data-ttu-id="40014-119">Daha fazla bilgi için bkz: [Windows .NET Framework'ü yüklemek](./install/index.md).</span><span class="sxs-lookup"><span data-stu-id="40014-119">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="40014-120">Bkz: [.NET Framework onarın](./install/repair.md) .NET Framework yüklenirken hatalarıyla karşılaşıyorsanız, .NET Framework yüklemenizi onarmak nasıl öğrenin.</span><span class="sxs-lookup"><span data-stu-id="40014-120">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you are experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="40014-121">.NET Framework yükleme hakkında daha ayrıntılı bilgi için bkz: [geliştiriciler için .NET Framework'ü yüklemek](../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="40014-121">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](../../docs/framework/install/guide-for-developers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40014-122">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="40014-122">In This Section</span></span>

[<span data-ttu-id="40014-123">Yenilikler</span><span class="sxs-lookup"><span data-stu-id="40014-123">What's New</span></span>](../../docs/framework/whats-new/index.md)  
<span data-ttu-id="40014-124">.NET Framework'ün en son sürümlerindeki yeni temel özellikleri ve değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="40014-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="40014-125">Kullanılmayan türlerin ve üyelerin listelerini içerir ve uygulamalarınızı .net Framework'ün önceki sürümünden yenisine geçirmek için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="40014-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>  
  
[<span data-ttu-id="40014-126">Başlarken</span><span class="sxs-lookup"><span data-stu-id="40014-126">Getting Started</span></span>](../../docs/framework/get-started/index.md)  
<span data-ttu-id="40014-127">.NET Framework'e kapsamlı bir genel bakış ve ek kaynaklara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="40014-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
<span data-ttu-id="40014-128">[Geçiş Kılavuzu](../../docs/framework/migration-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="40014-128">[Migration Guide](../../docs/framework/migration-guide/index.md) </span></span>  
<span data-ttu-id="40014-129">Kaynaklar ve uygulamanız .NET Framework'ün yeni bir sürüme geçiş, göz önünde bulundurmanız gereken değişiklikleri listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="40014-129">Provides resources and a list of changes you need to consider  if you're migrating your application to a new version of the .NET Framework.</span></span>  
  
[<span data-ttu-id="40014-130">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="40014-130">Development Guide</span></span>](../../docs/framework/development-guide.md)  
<span data-ttu-id="40014-131">Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="40014-131">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
[<span data-ttu-id="40014-132">Araçlar</span><span class="sxs-lookup"><span data-stu-id="40014-132">Tools</span></span>](../../docs/framework/tools/index.md)  
<span data-ttu-id="40014-133">.NET Framework teknolojilerini kullanarak uygulamalar geliştirmenize, yapılandırmanıza ve dağıtmanıza yardımcı olacak araçları açıklar.</span><span class="sxs-lookup"><span data-stu-id="40014-133">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>  
  
<span data-ttu-id="40014-134">[.NET framework sınıf kitaplığı](/dotnet/api/?view=netframework-4.7.1) </span><span class="sxs-lookup"><span data-stu-id="40014-134">[.NET Framework Class Library](/dotnet/api/?view=netframework-4.7.1) </span></span>  
<span data-ttu-id="40014-135">Sözdizimi, kod örnekleri ve .NET Framework isim uzaylarında bulunan her sınıf için ilgili bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="40014-135">Supplies syntax, code examples, and related information for each class contained in the .NET Framework namespaces.</span></span>  
  
[<span data-ttu-id="40014-136">Ek sınıf kitaplıkları ve API'ler</span><span class="sxs-lookup"><span data-stu-id="40014-136">Additional Class Libraries and APIs</span></span>](../../docs/framework/additional-apis/index.md)  
<span data-ttu-id="40014-137">Belirli platformlar veya uygulamaları .NET Framework'ün hedef sınıfları yanı sıra, bant dışı (OOB) sürümlerde bulunan sınıflar için belgeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="40014-137">Provides documentation for classes contained in out-of-band (OOB) releases, as well as for classes that target specific platforms or implementations of the .NET Framework.</span></span>
