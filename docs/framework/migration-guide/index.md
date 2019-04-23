---
title: '4.8, 4.7, 4.6 ve 4.5 .NET Framework Geçiş Kılavuzu '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb51a0be57992d65a88e958d76a5e371dc028a00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974967"
---
# <a name="migration-guide-to-the-net-framework-48-47-46-and-45"></a><span data-ttu-id="344cc-102">4.8, 4.7, 4.6 ve 4.5 .NET Framework Geçiş Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="344cc-102">Migration Guide to the .NET Framework 4.8, 4.7, 4.6, and 4.5</span></span>

<span data-ttu-id="344cc-103">Uygulamanızı .NET Framework'ün önceki bir sürümü kullanılarak oluşturuldu, bunu genellikle .NET Framework 4.5 için yükseltebilirsiniz ve nokta (4.5.1 ve 4.5.2'yi) sürümlerini .NET Framework 4.6 ve onun nokta sürümleri (4.6.1 ve 4.6.2), .NET Framework 4.7 ve onun nokta sürümleri) 4.7.1 ve 4.7.2) veya .NET Framework 4.8 kolayca.</span><span class="sxs-lookup"><span data-stu-id="344cc-103">If you created your app using an earlier version of the .NET Framework, you can generally upgrade it to .NET Framework 4.5 and its point releases (4.5.1 and 4.5.2), .NET Framework 4.6 and its point releases (4.6.1 and 4.6.2), .NET Framework 4.7 and its point releases (4.7.1 and 4.7.2), or .NET Framework 4.8 easily.</span></span> <span data-ttu-id="344cc-104">Projenizi Visual Studio'da açın.</span><span class="sxs-lookup"><span data-stu-id="344cc-104">Open your project in Visual Studio.</span></span> <span data-ttu-id="344cc-105">Projenizi Visual Studio'nun önceki bir sürümde oluşturulmuşsa **proje uygunluğu** iletişim kutusu otomatik olarak açılır.</span><span class="sxs-lookup"><span data-stu-id="344cc-105">If your project was created in an earlier version of Visual Studio, the **Project Compatibility** dialog box automatically opens.</span></span> <span data-ttu-id="344cc-106">Visual Studio'da bir proje yükseltme hakkında daha fazla bilgi için bkz. [bağlantı noktası, geçirme ve yükseltme Visual Studio projeleri](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) ve [Visual Studio 2019 Platform hedefleme ve Uyumluluk](/visualstudio/releases/2019/compatibility).</span><span class="sxs-lookup"><span data-stu-id="344cc-106">For more information about upgrading a project in Visual Studio, see [Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and [Visual Studio 2019 Platform Targeting and Compatibility](/visualstudio/releases/2019/compatibility).</span></span>

 <span data-ttu-id="344cc-107">Ancak, .NET Framework'teki bazı değişiklikler kodunuzda değişiklikler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="344cc-107">However, some changes in the .NET Framework require changes to your code.</span></span> <span data-ttu-id="344cc-108">.NET Framework 4.5 ve nokta sürümleri, .NET Framework 4.6 ve onun nokta sürümleri, .NET Framework 4.7 ve onun nokta sürümleri veya .NET Framework 4.8 yeni olan işlevsellikten yararlanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="344cc-108">You may also want to take advantage of functionality that is new in .NET Framework 4.5 and its point releases, in .NET Framework 4.6 and its point releases, in .NET Framework 4.7 and its point releases, or in .NET Framework 4.8.</span></span> <span data-ttu-id="344cc-109">.NET Framework'ün yeni bir sürümü, tipik olarak adlandırılır için uygulamanızda bu tür değişiklikleri yapmaya *geçiş*.</span><span class="sxs-lookup"><span data-stu-id="344cc-109">Making these types of changes to your app for a new version of the .NET Framework is typically referred to as *migration*.</span></span> <span data-ttu-id="344cc-110">Uygulamanızı geçişi sahip değilse, bu .NET Framework 4.5 veya sonraki bir sürümünü yeniden derlemeden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="344cc-110">If your app doesn't have to be migrated, you can run it in the .NET Framework 4.5 or a later version without recompiling it.</span></span>

## <a name="migration-resources"></a><span data-ttu-id="344cc-111">Geçiş kaynakları</span><span class="sxs-lookup"><span data-stu-id="344cc-111">Migration resources</span></span>

<span data-ttu-id="344cc-112">Uygulamanızı .NET Framework'ün önceki sürümlerinden 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 veya 4.8 sürümüne geçirmeden önce aşağıdaki belgeleri gözden geçirin:</span><span class="sxs-lookup"><span data-stu-id="344cc-112">Review the following documents before you migrate your app from earlier versions of the .NET Framework to version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, or 4.8:</span></span>

- <span data-ttu-id="344cc-113">Bkz: [sürümler ve bağımlılıklar](versions-and-dependencies.md) .NET Framework'ün her sürümü temelinde CLR sürümünü anlamak ve uygulamalarınızı başarıyla hedeflemekle yönergeleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="344cc-113">See [Versions and Dependencies](versions-and-dependencies.md) to understand the CLR version underlying each version of the .NET Framework and to review guidelines for targeting your apps successfully.</span></span>

- <span data-ttu-id="344cc-114">Gözden geçirme [uygulama uyumluluğu](application-compatibility.md) çalışma zamanı ve yeniden hedefleme değişiklikleri uygulamanız ve bunları nasıl ele alınacağını etkileyebilecek öğrenin.</span><span class="sxs-lookup"><span data-stu-id="344cc-114">Review [Application Compatibility](application-compatibility.md) to find out about runtime and retargeting changes that might affect your app and how to handle them.</span></span>

- <span data-ttu-id="344cc-115">Gözden geçirme [Sınıf Kitaplığı'nda ne kullanılmıyor](../whats-new/whats-obsolete.md) herhangi bir tür veya üyeleri geçersiz yapılan kodunuzu ve önerilen alternatifleri belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="344cc-115">Review [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md) to determine any types or members in your code that have been made obsolete, and the recommended alternatives.</span></span>

- <span data-ttu-id="344cc-116">Bkz: [yenilikler](../whats-new/index.md) uygulamanıza eklemek isteyebileceğiniz yeni özelliklerin açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="344cc-116">See [What's New](../whats-new/index.md) for descriptions of new features that you may want to add to your app.</span></span>

## <a name="see-also"></a><span data-ttu-id="344cc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="344cc-117">See also</span></span>

- [<span data-ttu-id="344cc-118">Uygulama Uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="344cc-118">Application Compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="344cc-119">.NET Framework 1.1'den Geçiş</span><span class="sxs-lookup"><span data-stu-id="344cc-119">Migrating from the .NET Framework 1.1</span></span>](migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="344cc-120">Sürüm Uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="344cc-120">Version Compatibility</span></span>](version-compatibility.md)
- [<span data-ttu-id="344cc-121">Sürümler ve Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="344cc-121">Versions and Dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="344cc-122">Nasıl yapılır: Bir uygulamayı .NET Framework 4 veya sonraki sürümler destekleyecek şekilde yapılandırma</span><span class="sxs-lookup"><span data-stu-id="344cc-122">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="344cc-123">Yenilikler</span><span class="sxs-lookup"><span data-stu-id="344cc-123">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="344cc-124">Sınıf Kitaplığında Artık Kullanılmayanlar</span><span class="sxs-lookup"><span data-stu-id="344cc-124">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
- [<span data-ttu-id="344cc-125">.NET framework sürüm ve derleme bilgileri</span><span class="sxs-lookup"><span data-stu-id="344cc-125">.NET Framework Version and Assembly Information</span></span>](https://go.microsoft.com/fwlink/?LinkId=201701)
- [<span data-ttu-id="344cc-126">Microsoft .NET Framework Destek Ömrü İlkesi</span><span class="sxs-lookup"><span data-stu-id="344cc-126">Microsoft .NET Framework Support Lifecycle Policy</span></span>](https://go.microsoft.com/fwlink/?LinkId=196607)
- [<span data-ttu-id="344cc-127">.NET Framework 4 geçiş sorunları</span><span class="sxs-lookup"><span data-stu-id="344cc-127">.NET Framework 4 migration issues</span></span>](net-framework-4-migration-issues.md)