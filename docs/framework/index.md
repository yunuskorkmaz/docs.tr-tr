---
title: .NET Çerçeve dokümantasyonu
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
ms.openlocfilehash: d94d97cd1b519025ff360dc903558ea3656818d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181529"
---
# <a name="net-framework-guide"></a><span data-ttu-id="700e3-102">.NET Framework kılavuzu</span><span class="sxs-lookup"><span data-stu-id="700e3-102">.NET Framework guide</span></span>

> [!NOTE]
> <span data-ttu-id="700e3-103">Bu .NET Framework içerik kümesi .NET Framework sürümleri 4.5 ile 4.8 için bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="700e3-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="700e3-104">.NET Framework'ü indirmek için [bkz.](./install/guide-for-developers.md)</span><span class="sxs-lookup"><span data-stu-id="700e3-104">To download .NET Framework, see [Install .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="700e3-105">.NET Framework'deki yeni özelliklerin ve değişikliklerin listesi için [bkz.](./whats-new/index.md)</span><span class="sxs-lookup"><span data-stu-id="700e3-105">For a list of new features and changes in .NET Framework, see [What's New in .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="700e3-106">Desteklenen platformların listesi için [bkz.](./get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="700e3-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="700e3-107">.NET Framework'ün eski sürümleriyle ilgili belgeler için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/)</span><span class="sxs-lookup"><span data-stu-id="700e3-107">For documentation about older versions of .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="700e3-108">.NET Framework, web, Windows, Windows Server ve Microsoft Azure için uygulamalar oluşturmak için bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="700e3-108">.NET Framework is a development platform for building apps for web, Windows, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="700e3-109">Ortak dil çalışma süresi (CLR) ve birçok endüstri standardı için geniş bir işlevsellik ve destek yelpazesi içeren .NET Framework sınıf kitaplığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="700e3-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="700e3-110">.NET Framework bellek yönetimi, tür ve bellek güvenliği, güvenlik, ağ ve uygulama dağıtımı dahil olmak üzere birçok hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="700e3-110">.NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="700e3-111">Alt düzey Windows işletim sistemini özetleyen kullanımı kolay veri yapıları ve API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="700e3-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="700e3-112">C#, F#ve Visual Basic dahil olmak üzere .NET Framework ile farklı programlama dilleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="700e3-112">You can use different programming languages with .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="700e3-113">Hem kullanıcılar hem de geliştiriciler için .NET Framework'e genel bir giriş için [başlarken](./get-started/index.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="700e3-113">For a general introduction to .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="700e3-114">.NET Framework'ün mimarisine ve temel özelliklerine giriş için [genel bakışa](./get-started/overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="700e3-114">For an introduction to the architecture and key features of .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="700e3-115">.NET Framework Docker ve [Windows Kapsayıcıları](/virtualization/windowscontainers/about/)ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="700e3-115">.NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span>

## <a name="installation"></a><span data-ttu-id="700e3-116">Yükleme</span><span class="sxs-lookup"><span data-stu-id="700e3-116">Installation</span></span>

<span data-ttu-id="700e3-117">.NET Framework, .NET Framework uygulamalarını çalıştırmanızı sağlayan Windows ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="700e3-117">.NET Framework comes with Windows, which enables you to run .NET Framework applications.</span></span> <span data-ttu-id="700e3-118">Windows sürümünüzle birlikte gelenden daha sonra .NET Framework sürümüne ihtiyacınız olabilir.</span><span class="sxs-lookup"><span data-stu-id="700e3-118">You may need a later version of .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="700e3-119">Daha fazla bilgi için [Windows'da Install .NET Framework](./install/index.md)'e bakın.</span><span class="sxs-lookup"><span data-stu-id="700e3-119">For more information, see [Install .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="700e3-120">Yükleme sırasında hatalar yaşıyorsanız .NET Framework yüklemenizi nasıl onarabileceğinizi öğrenmek için [Bkz.](./install/repair.md)</span><span class="sxs-lookup"><span data-stu-id="700e3-120">To learn how to repair your .NET Framework installation if you're experiencing errors during installation, see [Repair .NET Framework](./install/repair.md).</span></span>

<span data-ttu-id="700e3-121">.NET Framework'ü indirme hakkında daha ayrıntılı bilgi için [geliştiriciler için .NET Framework'ü yükleyin'](./install/guide-for-developers.md)e bakın.</span><span class="sxs-lookup"><span data-stu-id="700e3-121">For more detailed information on downloading .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="700e3-122">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="700e3-122">In this section</span></span>

* [<span data-ttu-id="700e3-123">Yenilikler</span><span class="sxs-lookup"><span data-stu-id="700e3-123">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="700e3-124">.NET Framework'ün en son sürümlerindeki yeni temel özellikleri ve değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="700e3-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="700e3-125">Kullanılmayan türlerin ve üyelerin listelerini içerir ve uygulamalarınızı .net Framework'ün önceki sürümünden yenisine geçirmek için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="700e3-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="700e3-126">Başlayın</span><span class="sxs-lookup"><span data-stu-id="700e3-126">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="700e3-127">.NET Framework'e kapsamlı bir genel bakış ve ek kaynaklara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="700e3-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="700e3-128">Kurulum Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="700e3-128">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="700e3-129">.NET Framework yükleme ve sorun giderme hakkında kaynaklar ve rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="700e3-129">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="700e3-130">Geçiş Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="700e3-130">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="700e3-131">Uygulamanızı .NET Framework'ün yeni bir sürümüne geçirerek göz önünde bulundurmanız gereken değişikliklerin listesini ve kaynakları sağlar.</span><span class="sxs-lookup"><span data-stu-id="700e3-131">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="700e3-132">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="700e3-132">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="700e3-133">Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="700e3-133">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="700e3-134">Araçlar</span><span class="sxs-lookup"><span data-stu-id="700e3-134">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="700e3-135">.NET Framework teknolojilerini kullanarak uygulamalar geliştirmenize, yapılandırmanıza ve dağıtmanıza yardımcı olacak araçları açıklar.</span><span class="sxs-lookup"><span data-stu-id="700e3-135">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="700e3-136">Ek sınıf kitaplıkları ve API'ler</span><span class="sxs-lookup"><span data-stu-id="700e3-136">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="700e3-137">Microsoft araçları tarafından kullanılan özel .NET Framework API'leri için belgeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="700e3-137">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="700e3-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="700e3-138">See also</span></span>

* [<span data-ttu-id="700e3-139">.NET Çerçeve Sınıf Kütüphanesi</span><span class="sxs-lookup"><span data-stu-id="700e3-139">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)
