---
title: ".NET Framework 4.7, 4.6 ve 4.5 Geçiş Kılavuzu "
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59c4ae2961b3e029ddd5f67afc9644042af95efb
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a><span data-ttu-id="b2003-102">.NET Framework 4.7, 4.6 ve 4.5 Geçiş Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b2003-102">Migration Guide to the .NET Framework 4.7, 4.6, and 4.5</span></span> 
<span data-ttu-id="b2003-103">.NET Framework'ün önceki bir sürümünü kullanarak uygulamanızı oluşturduysanız, genellikle, .NET Framework 4.5 ve kendi noktası sürümleri (4.5.1 ve 4.5.2), .NET Framework 4.6 ve onun noktası sürümleri (4.6.1 ve 4.6.2) veya .NET Framework 4.7 ve kendi noktası için yükseltebilirsiniz , .NET Framework 4.7.1, kolayca serbest bırakın.</span><span class="sxs-lookup"><span data-stu-id="b2003-103">If you created your app using an earlier version of the .NET Framework, you can generally upgrade it to the .NET Framework 4.5 and its point releases (4.5.1 and 4.5.2), the .NET Framework 4.6 and its point releases (4.6.1 and 4.6.2), or the .NET Framework 4.7 and its point release, the .NET Framework 4.7.1, easily.</span></span> <span data-ttu-id="b2003-104">Projenizi Visual Studio'da açın.</span><span class="sxs-lookup"><span data-stu-id="b2003-104">Open your project in Visual Studio.</span></span> <span data-ttu-id="b2003-105">Projeniz Visual Studio'nun daha önceki bir sürümünde oluşturulduysa **proje Uyumluluk** iletişim kutusu otomatik olarak açılır.</span><span class="sxs-lookup"><span data-stu-id="b2003-105">If your project was created in an earlier version of Visual Studio, the **Project Compatibility** dialog box automatically opens.</span></span> <span data-ttu-id="b2003-106">Visual Studio Proje yükseltme hakkında daha fazla bilgi için bkz: [bağlantı noktası, geçirme ve yükseltme Visual Studio projeleri](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) ve [Visual Studio 2017 Platform desteği ve Uyumluluk](/visualstudio/productinfo/vs2017-compatibility-vs).</span><span class="sxs-lookup"><span data-stu-id="b2003-106">For more information about upgrading a project in Visual Studio, see [Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and [Visual Studio 2017 Platform Targeting and Compatibility](/visualstudio/productinfo/vs2017-compatibility-vs).</span></span>  
  
 <span data-ttu-id="b2003-107">Ancak, bazı değişiklikler .NET Framework'teki kodunuzdaki değişiklikleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b2003-107">However, some changes in the .NET Framework require changes to your code.</span></span> <span data-ttu-id="b2003-108">.NET Framework 4.5 ve onun noktası sürümler, .NET Framework 4.6 ve onun noktası sürümleri veya .NET Framework 4.7 ve onun noktası sürüm, .NET Framework 4.7.1 yeni işlevsellikten yararlanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2003-108">You may also want to take advantage of functionality that is new in the .NET Framework 4.5 and its point releases, in the .NET Framework 4.6 and its point releases, or in the .NET Framework 4.7 and its point release, the .NET Framework 4.7.1.</span></span> <span data-ttu-id="b2003-109">Yeni bir .NET Framework sürümünü, tipik olarak adlandırılır için uygulamanızın bu tip değişiklikler yapma *geçiş*.</span><span class="sxs-lookup"><span data-stu-id="b2003-109">Making these types of changes to your app for a new version of the .NET Framework is typically referred to as *migration*.</span></span> <span data-ttu-id="b2003-110">Uygulamanızı geçirilecek yoksa, .NET Framework 4.5 veya sonraki bir sürümünü yeniden derlenmesi olmadan çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2003-110">If your app doesn't have to be migrated, you can run it in the .NET Framework 4.5 or a later version without recompiling it.</span></span>  
  
## <a name="migration-resources"></a><span data-ttu-id="b2003-111">Geçiş kaynakları</span><span class="sxs-lookup"><span data-stu-id="b2003-111">Migration resources</span></span>  
 <span data-ttu-id="b2003-112">Uygulamanızı sürüm 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 veya 4.7.1 .NET Framework'ün önceki sürümlerden geçirmeden önce şu belgeleri gözden geçirin:</span><span class="sxs-lookup"><span data-stu-id="b2003-112">Review the following documents before you migrate your app from earlier versions of the .NET Framework to version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, or 4.7.1:</span></span>  
  
-   <span data-ttu-id="b2003-113">Bkz: [sürümleri ve bağımlılıkları](../../../docs/framework/migration-guide/versions-and-dependencies.md) her .NET Framework sürümünü temel CLR sürümü anlamak ve uygulamalarınızı başarıyla hedefleme için yönergeleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="b2003-113">See [Versions and Dependencies](../../../docs/framework/migration-guide/versions-and-dependencies.md) to understand the CLR version underlying each version of the .NET Framework and to review guidelines for targeting your apps successfully.</span></span>  
  
-   <span data-ttu-id="b2003-114">Gözden geçirme [uygulama uyumluluğu](../../../docs/framework/migration-guide/application-compatibility.md) çalışma zamanı ve yeniden hedefleme uygulamanızı ve bunları nasıl ele alınacağını etkileyebilecek değişiklikleri hakkında bilgi almak için.</span><span class="sxs-lookup"><span data-stu-id="b2003-114">Review [Application Compatibility](../../../docs/framework/migration-guide/application-compatibility.md) to find out about runtime and retargeting changes that might affect your app and how to handle them.</span></span>  
  
-   <span data-ttu-id="b2003-115">Gözden geçirme [Sınıf Kitaplığı'nda ne kullanılmıyor](../../../docs/framework/whats-new/whats-obsolete.md) türleri veya kullanımdan kaldırmıştır kodunuzu ve önerilen Alternatiflerle üyeleri belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="b2003-115">Review [What's Obsolete in the Class Library](../../../docs/framework/whats-new/whats-obsolete.md) to determine any types or members in your code that have been made obsolete, and the recommended alternatives.</span></span>  
  
-   <span data-ttu-id="b2003-116">Bkz: [yenilikler](../../../docs/framework/whats-new/index.md) uygulamanıza eklemek isteyebilirsiniz yeni özelliklerin açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="b2003-116">See [What's New](../../../docs/framework/whats-new/index.md) for descriptions of new features that you may want to add to your app.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2003-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2003-117">See Also</span></span>  
 [<span data-ttu-id="b2003-118">Uygulama Uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="b2003-118">Application Compatibility</span></span>](../../../docs/framework/migration-guide/application-compatibility.md)  
 [<span data-ttu-id="b2003-119">.NET Framework 1.1'den Geçiş</span><span class="sxs-lookup"><span data-stu-id="b2003-119">Migrating from the .NET Framework 1.1</span></span>](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [<span data-ttu-id="b2003-120">Sürüm Uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="b2003-120">Version Compatibility</span></span>](../../../docs/framework/migration-guide/version-compatibility.md)  
 [<span data-ttu-id="b2003-121">Sürümler ve Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="b2003-121">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)  
 [<span data-ttu-id="b2003-122">Nasıl yapılır: Bir Uygulamayı .NET Framework 4 veya 4.5'i Destekleyecek Şekilde Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b2003-122">How to: Configure an App to Support .NET Framework 4 or 4.5</span></span>](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [<span data-ttu-id="b2003-123">Yenilikler</span><span class="sxs-lookup"><span data-stu-id="b2003-123">What's New</span></span>](../../../docs/framework/whats-new/index.md)  
 [<span data-ttu-id="b2003-124">Sınıf Kitaplığında Artık Kullanılmayanlar</span><span class="sxs-lookup"><span data-stu-id="b2003-124">What's Obsolete in the Class Library</span></span>](../../../docs/framework/whats-new/whats-obsolete.md)  
 [<span data-ttu-id="b2003-125">.NET framework sürümünü ve derleme bilgileri</span><span class="sxs-lookup"><span data-stu-id="b2003-125">.NET Framework Version and Assembly Information</span></span>](http://go.microsoft.com/fwlink/?LinkId=201701)  
 <span data-ttu-id="b2003-126">[Microsoft .NET Framework destek yaşam döngüsü ilkesi](http://go.microsoft.com/fwlink/?LinkId=196607) [.NET Framework 4 geçiş sorunları](net-framework-4-migration-issues.md)</span><span class="sxs-lookup"><span data-stu-id="b2003-126">[Microsoft .NET Framework Support Lifecycle Policy](http://go.microsoft.com/fwlink/?LinkId=196607) [.NET Framework 4 migration issues](net-framework-4-migration-issues.md)</span></span>
