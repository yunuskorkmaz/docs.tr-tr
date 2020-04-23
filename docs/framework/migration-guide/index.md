---
title: '.NET Framework 4.8, 4.7, 4.6 ve 4.5 Geçiş Kılavuzu '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: fbaee646f7adcfe1a53d4231790e4258fd95a892
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102638"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a><span data-ttu-id="9b387-102">.NET Framework 4.8, 4.7, 4.6 ve 4.5'e geçiş</span><span class="sxs-lookup"><span data-stu-id="9b387-102">Migrate to .NET Framework 4.8, 4.7, 4.6, and 4.5</span></span>

<span data-ttu-id="9b387-103">Uygulamanızı .NET Framework'ün önceki bir sürümünü kullanarak oluşturduysanız, genellikle .NET Framework 4.5 ve puan sürümleri (4.5.1 ve 4.5.2), .NET Framework 4.6 ve puan sürümleri (4.6.1 ve 4.6.2), .NET Framework 4.7 ve puan sürümleri (4.7.1 ve 4.7.2) veya .NET Framework 4.8'e kolayca yükseltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b387-103">If you created your app using an earlier version of .NET Framework, you can generally upgrade it to .NET Framework 4.5 and its point releases (4.5.1 and 4.5.2), .NET Framework 4.6 and its point releases (4.6.1 and 4.6.2), .NET Framework 4.7 and its point releases (4.7.1 and 4.7.2), or .NET Framework 4.8 easily.</span></span> <span data-ttu-id="9b387-104">Görsel Stüdyo'da projenizi açın.</span><span class="sxs-lookup"><span data-stu-id="9b387-104">Open your project in Visual Studio.</span></span> <span data-ttu-id="9b387-105">Projeniz Visual Studio'nun önceki bir sürümünde oluşturulduysa, **Proje Uyumluluğu** iletişim kutusu otomatik olarak açılır.</span><span class="sxs-lookup"><span data-stu-id="9b387-105">If your project was created in an earlier version of Visual Studio, the **Project Compatibility** dialog box automatically opens.</span></span> <span data-ttu-id="9b387-106">Visual Studio'da bir projeyi yükseltme hakkında daha fazla bilgi için, [Visual Studio Projeleri ve Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) [2019 Platform Hedefleme ve Uyumluluğu](/visualstudio/releases/2019/compatibility)Geliştirme hakkında bakınız.</span><span class="sxs-lookup"><span data-stu-id="9b387-106">For more information about upgrading a project in Visual Studio, see [Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and [Visual Studio 2019 Platform Targeting and Compatibility](/visualstudio/releases/2019/compatibility).</span></span>

 <span data-ttu-id="9b387-107">Ancak, .NET Framework'deki bazı değişiklikler için kodunuzda değişiklik gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b387-107">However, some changes in .NET Framework require changes to your code.</span></span> <span data-ttu-id="9b387-108">Ayrıca .NET Framework 4.5 ve onun nokta sürümlerinde,.NET Framework 4.6 ve onun nokta sürümlerinde, .NET Framework 4.7 ve onun puan sürümlerinde veya .NET Framework 4.8'de yeni olan işlevselliklerden yararlanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b387-108">You may also want to take advantage of functionality that is new in .NET Framework 4.5 and its point releases, in .NET Framework 4.6 and its point releases, in .NET Framework 4.7 and its point releases, or in .NET Framework 4.8.</span></span> <span data-ttu-id="9b387-109">.NET Framework'ün yeni bir sürümü için uygulamanızda bu tür değişiklikler yapmak genellikle *geçiş*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9b387-109">Making these types of changes to your app for a new version of .NET Framework is typically referred to as *migration*.</span></span> <span data-ttu-id="9b387-110">Uygulamanızın geçirilmeniz gerekiyorsa, uygulamayı yeniden derlemeden .NET Framework 4.5 veya daha sonraki bir sürümde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b387-110">If your app doesn't have to be migrated, you can run it in .NET Framework 4.5 or a later version without recompiling it.</span></span>

## <a name="migration-resources"></a><span data-ttu-id="9b387-111">Geçiş kaynakları</span><span class="sxs-lookup"><span data-stu-id="9b387-111">Migration resources</span></span>

<span data-ttu-id="9b387-112">Uygulamanızı .NET Framework'ün önceki sürümlerinden sürüm 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 veya 4.8 sürümüne geçirmeden önce aşağıdaki belgeleri inceleyin:</span><span class="sxs-lookup"><span data-stu-id="9b387-112">Review the following documents before you migrate your app from earlier versions of .NET Framework to version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, or 4.8:</span></span>

- <span data-ttu-id="9b387-113">.NET Framework'ün her sürümünün altında yatan CLR sürümünü anlamak ve uygulamalarınızı başarıyla hedefleme yönergelerini gözden geçirmek için [Sürümler ve Bağımlılıklar'a](versions-and-dependencies.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="9b387-113">See [Versions and Dependencies](versions-and-dependencies.md) to understand the CLR version underlying each version of the .NET Framework and to review guidelines for targeting your apps successfully.</span></span>

- <span data-ttu-id="9b387-114">Uygulamanızı etkileyebilecek çalışma zamanı ve yeniden hedefleme değişiklikleri ve bunları nasıl işleyeceğiniöğrenmek için [Uygulama uyumluluğunu](application-compatibility.md) gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="9b387-114">Review [Application compatibility](application-compatibility.md) to find out about runtime and retargeting changes that might affect your app and how to handle them.</span></span>

- <span data-ttu-id="9b387-115">Kodunuzda geçersiz kılınan türleri veya üyeleri ve önerilen alternatifleri belirlemek için [Sınıf Kitaplığında Eski olanları](../whats-new/whats-obsolete.md) gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="9b387-115">Review [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md) to determine any types or members in your code that have been made obsolete, and the recommended alternatives.</span></span>

- <span data-ttu-id="9b387-116">Uygulamanıza eklemek isteyebileceğiniz yeni özelliklerin açıklamaları için [Yeniliklere](../whats-new/index.md) Bakın.</span><span class="sxs-lookup"><span data-stu-id="9b387-116">See [What's New](../whats-new/index.md) for descriptions of new features that you may want to add to your app.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b387-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b387-117">See also</span></span>

- [<span data-ttu-id="9b387-118">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="9b387-118">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="9b387-119">.NET Framework 1.1'den Geçiş</span><span class="sxs-lookup"><span data-stu-id="9b387-119">Migrating from the .NET Framework 1.1</span></span>](migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="9b387-120">Sürüm Uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="9b387-120">Version Compatibility</span></span>](version-compatibility.md)
- [<span data-ttu-id="9b387-121">Sürümler ve Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="9b387-121">Versions and Dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="9b387-122">Nasıl yapilir: Bir uygulamayı .NET Framework 4 veya sonraki sürümlerini destekleyecek şekilde yapılandırın</span><span class="sxs-lookup"><span data-stu-id="9b387-122">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="9b387-123">Yenilikler</span><span class="sxs-lookup"><span data-stu-id="9b387-123">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="9b387-124">Sınıf Kitaplığı'nda Artık Kullanılmayanlar</span><span class="sxs-lookup"><span data-stu-id="9b387-124">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
- [<span data-ttu-id="9b387-125">.NET Framework resmi destek politikası</span><span class="sxs-lookup"><span data-stu-id="9b387-125">.NET Framework official support policy</span></span>](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [<span data-ttu-id="9b387-126">.NET Framework 4 geçiş sorunları</span><span class="sxs-lookup"><span data-stu-id="9b387-126">.NET Framework 4 migration issues</span></span>](net-framework-4-migration-issues.md)
