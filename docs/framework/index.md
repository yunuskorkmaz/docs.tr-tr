---
title: .NET Framework belgeleri
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
ms.openlocfilehash: e5a86b3abf821a37944a0e478d0bc8f1bea31ccb
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699047"
---
# <a name="net-framework-guide"></a><span data-ttu-id="101ac-102">.NET Framework Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="101ac-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="101ac-103">Bu .NET Framework içerik kümesi, 4,5 ile 4,8 arasındaki .NET Framework sürümleri için bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="101ac-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="101ac-104">.NET Framework indirmek için, bkz. [.NET Framework yükleme](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="101ac-104">To download the .NET Framework, see [Installing the .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="101ac-105">Ağ çerçevesindeki yeni özelliklerin ve değişikliklerin listesi için bkz. [.NET Framework](./whats-new/index.md)yenilikler.</span><span class="sxs-lookup"><span data-stu-id="101ac-105">For a list of new features and changes in the NET Framework, see [What's New in the .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="101ac-106">Desteklenen platformların listesi için bkz. [sistem gereksinimleri .NET Framework](./get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="101ac-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="101ac-107">.NET Framework eski sürümleri hakkındaki belgeler için bkz. [.NET önceki sürümler belgeleri](https://docs.microsoft.com/previous-versions/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="101ac-107">For documentation about older versions of the .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="101ac-108">.NET Framework Web, Windows, Windows Phone, Windows Server ve Microsoft Azure için uygulama oluşturmaya yönelik bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="101ac-108">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="101ac-109">Birçok sektör standardı için çok çeşitli işlevler ve destek içeren ortak dil çalışma zamanı (CLR) ve .NET Framework sınıf kitaplığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="101ac-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="101ac-110">.NET Framework bellek yönetimi, tür ve bellek güvenliği, güvenlik, ağ ve uygulama dağıtımı dahil olmak üzere birçok hizmeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="101ac-110">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="101ac-111">Bu, alt düzey Windows işletim sistemini soyutlamak için kullanımı kolay veri yapıları ve API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="101ac-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="101ac-112">, Ve Visual Basic dahil olmak üzere C# F#.NET Framework farklı programlama dilleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="101ac-112">You can use different programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="101ac-113">Hem kullanıcılar hem de geliştiriciler için .NET Framework genel bir giriş için [bkz. Başlarken](./get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="101ac-113">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="101ac-114">.NET Framework mimarisine ve temel özelliklerine giriş için bkz. [genel bakış](./get-started/overview.md).</span><span class="sxs-lookup"><span data-stu-id="101ac-114">For an introduction to the architecture and key features of the .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="101ac-115">.NET Framework, Docker ve [Windows kapsayıcıları](/virtualization/windowscontainers/about/)ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="101ac-115">The .NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span>

## <a name="installation"></a><span data-ttu-id="101ac-116">Yükleme</span><span class="sxs-lookup"><span data-stu-id="101ac-116">Installation</span></span>

<span data-ttu-id="101ac-117">.NET Framework, Windows ile birlikte gelir ve .NET Framework uygulamaları çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="101ac-117">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="101ac-118">.NET Framework, Windows sürümünüzle birlikte gelen bir sonraki sürümüne ihtiyacınız olabilir.</span><span class="sxs-lookup"><span data-stu-id="101ac-118">You may need a later version of the .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="101ac-119">Daha fazla bilgi için, bkz. [.NET Framework Windows 'A Install](./install/index.md).</span><span class="sxs-lookup"><span data-stu-id="101ac-119">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="101ac-120">.NET Framework yüklerken hata yaşıyorsanız .NET Framework yüklemenizi onarmayı öğrenmek için bkz. [.NET Framework onarma](./install/repair.md) .</span><span class="sxs-lookup"><span data-stu-id="101ac-120">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you're experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="101ac-121">.NET Framework indirme hakkında daha ayrıntılı bilgi için bkz. [geliştiricilere yönelik .NET Framework yükleme](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="101ac-121">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="101ac-122">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="101ac-122">In this section</span></span>

* [<span data-ttu-id="101ac-123">Yenilikler</span><span class="sxs-lookup"><span data-stu-id="101ac-123">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="101ac-124">.NET Framework'ün en son sürümlerindeki yeni temel özellikleri ve değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="101ac-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="101ac-125">Kullanılmayan türlerin ve üyelerin listelerini içerir ve uygulamalarınızı .net Framework'ün önceki sürümünden yenisine geçirmek için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="101ac-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="101ac-126">Başlarken</span><span class="sxs-lookup"><span data-stu-id="101ac-126">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="101ac-127">.NET Framework'e kapsamlı bir genel bakış ve ek kaynaklara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="101ac-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="101ac-128">Yükleme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="101ac-128">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="101ac-129">.NET Framework yükleme ve sorun giderme hakkında kaynak ve kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="101ac-129">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="101ac-130">Geçiş Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="101ac-130">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="101ac-131">Uygulamanızı .NET Framework yeni bir sürümüne geçirdiğinizde göz önünde bulundurmanız gereken kaynak ve değişikliklerin listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="101ac-131">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="101ac-132">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="101ac-132">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="101ac-133">Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="101ac-133">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="101ac-134">Araçlar</span><span class="sxs-lookup"><span data-stu-id="101ac-134">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="101ac-135">.NET Framework teknolojilerini kullanarak uygulamalar geliştirmenize, yapılandırmanıza ve dağıtmanıza yardımcı olacak araçları açıklar.</span><span class="sxs-lookup"><span data-stu-id="101ac-135">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="101ac-136">Ek sınıf kitaplıkları ve API'ler</span><span class="sxs-lookup"><span data-stu-id="101ac-136">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="101ac-137">Microsoft araçları tarafından kullanılan özel .NET Framework API 'Leri için belgeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="101ac-137">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="101ac-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="101ac-138">See also</span></span>

- [<span data-ttu-id="101ac-139">.NET Framework sınıf kitaplığı</span><span class="sxs-lookup"><span data-stu-id="101ac-139">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)
