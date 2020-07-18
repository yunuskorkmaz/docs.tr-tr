---
title: '4,8, 4,7, 4,6 ve 4,5 .NET Framework geçiş kılavuzu '
description: Yeni özellikler ve uygulama uyumluluğuna yönelik kaynakları içeren daha yeni .NET Framework sürümlere geçirmeye yönelik bir kılavuz.
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: a5b632824efacdb5e99228727b8751dc7f17d363
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86443422"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a><span data-ttu-id="8d3ca-103">.NET Framework 4,8, 4,7, 4,6 ve 4,5 'e geçirin</span><span class="sxs-lookup"><span data-stu-id="8d3ca-103">Migrate to .NET Framework 4.8, 4.7, 4.6, and 4.5</span></span>

<span data-ttu-id="8d3ca-104">Uygulamanızı daha önceki bir .NET Framework sürümünü kullanarak oluşturduysanız, genellikle bunu .NET Framework 4,5 ve onun nokta sürümleri (4.5.1 ve 4.5.2), .NET Framework 4,6 ve nokta sürümleri (4.6.1 ve 4.6.2), .NET Framework 4,7 ve kendi nokta sürümleri (4.7.1 ve 4.7.2) ya da 4,8 .NET Framework kolayca yükseltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d3ca-104">If you created your app using an earlier version of .NET Framework, you can generally upgrade it to .NET Framework 4.5 and its point releases (4.5.1 and 4.5.2), .NET Framework 4.6 and its point releases (4.6.1 and 4.6.2), .NET Framework 4.7 and its point releases (4.7.1 and 4.7.2), or .NET Framework 4.8 easily.</span></span> <span data-ttu-id="8d3ca-105">Projenizi Visual Studio’da açın.</span><span class="sxs-lookup"><span data-stu-id="8d3ca-105">Open your project in Visual Studio.</span></span> <span data-ttu-id="8d3ca-106">Projeniz Visual Studio 'nun önceki bir sürümünde oluşturulduysa, **Proje uyumluluğu** iletişim kutusu otomatik olarak açılır.</span><span class="sxs-lookup"><span data-stu-id="8d3ca-106">If your project was created in an earlier version of Visual Studio, the **Project Compatibility** dialog box automatically opens.</span></span> <span data-ttu-id="8d3ca-107">Visual Studio 'da bir projeyi yükseltme hakkında daha fazla bilgi için bkz. [bağlantı noktası, geçiş ve yükseltme Visual Studio projeleri](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) ve [Visual Studio 2019 Platform hedefleme ve uyumluluk](/visualstudio/releases/2019/compatibility).</span><span class="sxs-lookup"><span data-stu-id="8d3ca-107">For more information about upgrading a project in Visual Studio, see [Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and [Visual Studio 2019 Platform Targeting and Compatibility](/visualstudio/releases/2019/compatibility).</span></span>

 <span data-ttu-id="8d3ca-108">Ancak .NET Framework yapılan bazı değişiklikler kodunuzda değişiklik yapılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8d3ca-108">However, some changes in .NET Framework require changes to your code.</span></span> <span data-ttu-id="8d3ca-109">Ayrıca, .NET Framework 4,5 ' deki ve nokta sürümlerindeki yeni işlevsellikten yararlanmak isteyebilirsiniz .NET Framework 4,6 ve onun nokta sürümleri, .NET Framework 4,7 ve onun nokta sürümleri, .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="8d3ca-109">You may also want to take advantage of functionality that is new in .NET Framework 4.5 and its point releases, in .NET Framework 4.6 and its point releases, in .NET Framework 4.7 and its point releases, or in .NET Framework 4.8.</span></span> <span data-ttu-id="8d3ca-110">.NET Framework yeni bir sürümü için uygulamanızda bu tür değişiklikler yapmak genellikle *geçiş*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8d3ca-110">Making these types of changes to your app for a new version of .NET Framework is typically referred to as *migration*.</span></span> <span data-ttu-id="8d3ca-111">Uygulamanızın geçirilmesi gerekiyorsa, bunu yeniden derlemeden .NET Framework 4,5 veya sonraki bir sürümde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d3ca-111">If your app doesn't have to be migrated, you can run it in .NET Framework 4.5 or a later version without recompiling it.</span></span>

## <a name="migration-resources"></a><span data-ttu-id="8d3ca-112">Geçiş kaynakları</span><span class="sxs-lookup"><span data-stu-id="8d3ca-112">Migration resources</span></span>

<span data-ttu-id="8d3ca-113">Uygulamanızı önceki .NET Framework sürümlerinden 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 veya 4,8 sürümüne geçirmeden önce aşağıdaki belgeleri gözden geçirin:</span><span class="sxs-lookup"><span data-stu-id="8d3ca-113">Review the following documents before you migrate your app from earlier versions of .NET Framework to version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, or 4.8:</span></span>

- <span data-ttu-id="8d3ca-114">.NET Framework her bir sürümünü temel alan CLR sürümünü anlamak ve uygulamalarınızı başarıyla hedeflemek için yönergeleri gözden geçirmek için [sürümler ve bağımlılıklar](versions-and-dependencies.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8d3ca-114">See [Versions and Dependencies](versions-and-dependencies.md) to understand the CLR version underlying each version of the .NET Framework and to review guidelines for targeting your apps successfully.</span></span>

- <span data-ttu-id="8d3ca-115">Uygulamanızı etkileyebilecek çalışma zamanı ve yeniden hedefleme değişiklikleri hakkında bilgi edinmek için [uygulama uyumluluğunu](application-compatibility.md) gözden geçirin ve bunları nasıl işleyebileceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="8d3ca-115">Review [Application compatibility](application-compatibility.md) to find out about runtime and retargeting changes that might affect your app and how to handle them.</span></span>

- <span data-ttu-id="8d3ca-116">Kodunuzda, kullanımdan kalkmış olan herhangi bir tür veya üyeyi ve önerilen alternatifleri belirlemek için, [Sınıf kitaplığındaki kullanım dışı olanları](../whats-new/whats-obsolete.md) gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="8d3ca-116">Review [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md) to determine any types or members in your code that have been made obsolete, and the recommended alternatives.</span></span>

- <span data-ttu-id="8d3ca-117">Uygulamanıza eklemek isteyebileceğiniz yeni özelliklerin [açıklamaları için bkz. yenilikler.](../whats-new/index.md)</span><span class="sxs-lookup"><span data-stu-id="8d3ca-117">See [What's New](../whats-new/index.md) for descriptions of new features that you may want to add to your app.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d3ca-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d3ca-118">See also</span></span>

- [<span data-ttu-id="8d3ca-119">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="8d3ca-119">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="8d3ca-120">.NET Framework 1.1'den Geçiş</span><span class="sxs-lookup"><span data-stu-id="8d3ca-120">Migrating from the .NET Framework 1.1</span></span>](migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="8d3ca-121">Sürüm uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="8d3ca-121">Version Compatibility</span></span>](version-compatibility.md)
- [<span data-ttu-id="8d3ca-122">Sürümler ve bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="8d3ca-122">Versions and Dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="8d3ca-123">Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8d3ca-123">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="8d3ca-124">Yenilikler</span><span class="sxs-lookup"><span data-stu-id="8d3ca-124">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="8d3ca-125">Sınıf Kitaplığı'nda Artık Kullanılmayanlar</span><span class="sxs-lookup"><span data-stu-id="8d3ca-125">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
- [<span data-ttu-id="8d3ca-126">.NET Framework resmi destek ilkesi</span><span class="sxs-lookup"><span data-stu-id="8d3ca-126">.NET Framework official support policy</span></span>](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [<span data-ttu-id="8d3ca-127">.NET Framework 4 geçiş sorunları</span><span class="sxs-lookup"><span data-stu-id="8d3ca-127">.NET Framework 4 migration issues</span></span>](net-framework-4-migration-issues.md)
