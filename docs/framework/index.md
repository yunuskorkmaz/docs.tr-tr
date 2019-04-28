---
title: .NET framework belgeleri
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6e21d2514ad357c906885750d9320575bdb75b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643939"
---
# <a name="net-framework-guide"></a><span data-ttu-id="e75e5-102">.NET Framework Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e75e5-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="e75e5-103">Bu .NET Framework İçerik kümesi, .NET Framework sürüm 4.5 4.8 aracılığıyla için bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="e75e5-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="e75e5-104">.NET Framework'ü indirmek için bkz [.NET Framework yükleme](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="e75e5-104">To download the .NET Framework, see [Installing the .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="e75e5-105">.NET Framework'daki yeni özellikler ve değişiklikleri listesi için bkz. [.NET Framework'teki yenilikler](./whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="e75e5-105">For a list of new features and changes in the NET Framework, see [What's New in the .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="e75e5-106">Desteklenen platformlar listesi için bkz. [.NET Framework System Requirements](./get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e75e5-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="e75e5-107">.NET Framework'ün daha eski sürümleri hakkında daha fazla bilgi için bkz [.NET önceki sürümlerin belgeleri](https://docs.microsoft.com/previous-versions/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="e75e5-107">For documentation about older versions of the .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="e75e5-108">.NET Framework web, Windows, Windows Phone, Windows Server ve Microsoft Azure için uygulama oluşturmaya yönelik bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="e75e5-108">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="e75e5-109">Ortak dil çalışma zamanı (CLR) ve geniş bir işlevsellik ve birçok sektör standartları desteği içeren .NET Framework sınıf kitaplığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="e75e5-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="e75e5-110">.NET Framework bellek yönetimi, türü ve bellek emniyet, güvenlik, ağ ve uygulama dağıtımı gibi birçok hizmet sunar.</span><span class="sxs-lookup"><span data-stu-id="e75e5-110">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="e75e5-111">Bu, kullanımı kolay veri yapıları ve alt düzey Windows işletim sistemi soyut API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e75e5-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="e75e5-112">.NET Framework ile kullanabileceğiniz farklı programlama dilleri dahil olmak üzere C#, F#ve Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e75e5-112">You can use different programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="e75e5-113">Kullanıcılara ve geliştiricilere yönelik .NET Framework'e Genel bir giriş için bkz: [Başlarken](./get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="e75e5-113">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="e75e5-114">Mimarisi ve .NET Framework'ün temel özelliklerine bir giriş için bkz [genel bakış](./get-started/overview.md).</span><span class="sxs-lookup"><span data-stu-id="e75e5-114">For an introduction to the architecture and key features of the .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="e75e5-115">.NET Framework ve Docker ile kullanılan [Windows kapsayıcıları](/virtualization/windowscontainers/about/).</span><span class="sxs-lookup"><span data-stu-id="e75e5-115">The .NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span> <span data-ttu-id="e75e5-116">Bkz: [dağıtma .NET Framework uygulamaları ile Docker](./docker/index.md) uygulamalarınızı Docker kapsayıcılarında çalıştırmak hakkında bilgi edinmek için.</span><span class="sxs-lookup"><span data-stu-id="e75e5-116">See [Deploying .NET Framework applications with Docker](./docker/index.md) to learn how to run your applications in Docker containers.</span></span>

## <a name="installation"></a><span data-ttu-id="e75e5-117">Yükleme</span><span class="sxs-lookup"><span data-stu-id="e75e5-117">Installation</span></span>

<span data-ttu-id="e75e5-118">.NET Framework, .NET Framework uygulamalarını çalıştırmanıza olanak sağlayan Windows ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="e75e5-118">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="e75e5-119">.NET Framework'ün sonraki bir sürümü, Windows sürümünüzle birlikte gelen bir gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e75e5-119">You may need a later version of the .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="e75e5-120">Daha fazla bilgi için [Windows üzerinde .NET Framework yükleme](./install/index.md).</span><span class="sxs-lookup"><span data-stu-id="e75e5-120">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="e75e5-121">Bkz: [.NET Framework'ü onarma](./install/repair.md) .NET Framework'ü yüklerken hataları yaşıyorsanız, .NET Framework yüklemenizi onarın hakkında bilgi edinmek için.</span><span class="sxs-lookup"><span data-stu-id="e75e5-121">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you're experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="e75e5-122">.NET Framework yükleme hakkında daha ayrıntılı bilgi için bkz: [geliştiriciler için .NET Framework yükleme](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="e75e5-122">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e75e5-123">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="e75e5-123">In this section</span></span>

* [<span data-ttu-id="e75e5-124">Yenilikler</span><span class="sxs-lookup"><span data-stu-id="e75e5-124">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="e75e5-125">.NET Framework'ün en son sürümlerindeki yeni temel özellikleri ve değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e75e5-125">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="e75e5-126">Kullanılmayan türlerin ve üyelerin listelerini içerir ve uygulamalarınızı .net Framework'ün önceki sürümünden yenisine geçirmek için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="e75e5-126">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="e75e5-127">Başlarken</span><span class="sxs-lookup"><span data-stu-id="e75e5-127">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="e75e5-128">.NET Framework'e kapsamlı bir genel bakış ve ek kaynaklara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e75e5-128">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="e75e5-129">Yükleme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e75e5-129">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="e75e5-130">Kaynaklar ve .NET Framework yükleme ve sorun giderme hakkında rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="e75e5-130">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="e75e5-131">Geçiş Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e75e5-131">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="e75e5-132">Kaynaklar ve uygulamanızı .NET Framework'ün yeni bir sürüme geçiş yapıyorsanız, dikkate almanız gereken değişikliklerin bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e75e5-132">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="e75e5-133">Docker Üzerinde .NET Framework Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e75e5-133">.NET Framework on Docker Guide</span></span>](./docker/index.md)  
<span data-ttu-id="e75e5-134">Windows kapsayıcıları kullanarak Docker ile .NET Framework uygulamaları çalıştırmak için kaynaklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e75e5-134">Provides resources to run .NET Framework applications with Docker, using Windows Containers.</span></span>

* [<span data-ttu-id="e75e5-135">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e75e5-135">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="e75e5-136">Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="e75e5-136">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="e75e5-137">Araçlar</span><span class="sxs-lookup"><span data-stu-id="e75e5-137">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="e75e5-138">.NET Framework teknolojilerini kullanarak uygulamalar geliştirmenize, yapılandırmanıza ve dağıtmanıza yardımcı olacak araçları açıklar.</span><span class="sxs-lookup"><span data-stu-id="e75e5-138">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="e75e5-139">Ek sınıf kitaplıkları ve API'ler</span><span class="sxs-lookup"><span data-stu-id="e75e5-139">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="e75e5-140">Microsoft araçları tarafından kullanılan özel .NET Framework API için belgeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e75e5-140">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="e75e5-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e75e5-141">See also</span></span>

* [<span data-ttu-id="e75e5-142">.NET framework sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="e75e5-142">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)