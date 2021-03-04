---
title: .NET Yükseltme Yardımcısı 'na genel bakış
description: .NET Framework geçiş ve projelerinizi .NET 5 ' e yükseltmelerine yardımcı olan .NET Yükseltme Yardımcısı aracına giriş.
author: ardalis
ms.date: 02/25/2021
ms.openlocfilehash: bd1c904586d170d93b76ae058914adb334289f89
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102108685"
---
# <a name="overview-of-the-net-upgrade-assistant"></a><span data-ttu-id="f498e-103">.NET Yükseltme Yardımcısı 'na genel bakış</span><span class="sxs-lookup"><span data-stu-id="f498e-103">Overview of the .NET Upgrade Assistant</span></span>

<span data-ttu-id="f498e-104">Şu anda .NET 5 ' e taşıma konusunda ilgilendiğiniz .NET Framework çalışan uygulamalarınız olabilir.</span><span class="sxs-lookup"><span data-stu-id="f498e-104">You might have apps that currently run on the .NET Framework that you're interested in porting to .NET 5.</span></span> <span data-ttu-id="f498e-105">.NET Yükseltme Yardımcısı aracı bu işleme yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f498e-105">The .NET Upgrade Assistant tool can assist with this process.</span></span> <span data-ttu-id="f498e-106">Bu makalede aşağıdakiler sunulmaktadır:</span><span class="sxs-lookup"><span data-stu-id="f498e-106">This article provides:</span></span>

* <span data-ttu-id="f498e-107">.NET Yükseltme Yardımcısı 'na genel bakış.</span><span class="sxs-lookup"><span data-stu-id="f498e-107">An overview of the .NET Upgrade Assistant.</span></span>
* <span data-ttu-id="f498e-108">.NET Yükseltme Yardımcısı 'Nı nasıl yükleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f498e-108">How to install the .NET Upgrade Assistant.</span></span>

## <a name="what-is-the-net-upgrade-assistant"></a><span data-ttu-id="f498e-109">.NET Yükseltme Yardımcısı nedir?</span><span class="sxs-lookup"><span data-stu-id="f498e-109">What is the .NET Upgrade Assistant</span></span>

<span data-ttu-id="f498e-110">.NET Yükseltme Yardımcısı, farklı türlerde .NET Framework uygulamalarda çalıştırılabilen bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="f498e-110">The .NET Upgrade Assistant is a command-line tool that can be run on different kinds of .NET Framework apps.</span></span> <span data-ttu-id="f498e-111">.NET Framework uygulamalarını .NET 5 ' e yükseltmeye yardımcı olmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f498e-111">It's designed to assist with upgrading .NET Framework apps to .NET 5.</span></span> <span data-ttu-id="f498e-112">Araç çalıştırıldıktan sonra, **çoğu durumda uygulama geçişi tamamlamaya daha fazla çaba gerektirir**.</span><span class="sxs-lookup"><span data-stu-id="f498e-112">After running the tool, **in most cases the app will require more effort to complete the migration**.</span></span> <span data-ttu-id="f498e-113">Araç, geçişin tamamlanmasına yardımcı olabilecek çözümleyiciler yüklemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="f498e-113">The tool includes the installation of analyzers that can assist with completing the migration.</span></span>

<span data-ttu-id="f498e-114">Şu anda araç şu .NET Framework uygulama türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="f498e-114">Currently the tool supports the following .NET Framework app types:</span></span>

- <span data-ttu-id="f498e-115">.NET Framework Windows Forms uygulamalar</span><span class="sxs-lookup"><span data-stu-id="f498e-115">.NET Framework Windows Forms apps</span></span>
- <span data-ttu-id="f498e-116">WPF uygulamalarını .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f498e-116">.NET Framework WPF apps</span></span>
- <span data-ttu-id="f498e-117">.NET Framework ASP.NET MVC uygulamaları</span><span class="sxs-lookup"><span data-stu-id="f498e-117">.NET Framework ASP.NET MVC apps</span></span>
- <span data-ttu-id="f498e-118">.NET Framework konsol uygulamaları</span><span class="sxs-lookup"><span data-stu-id="f498e-118">.NET Framework console apps</span></span>
- <span data-ttu-id="f498e-119">.NET Framework sınıf kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="f498e-119">.NET Framework class libraries</span></span>

<span data-ttu-id="f498e-120">.NET Yükseltme Yardımcısı şu anda ön sürüme sahiptir ve sık sık güncelleştirmeler alıyor.</span><span class="sxs-lookup"><span data-stu-id="f498e-120">The .NET Upgrade Assistant is currently prerelease and is receiving frequent updates.</span></span> <span data-ttu-id="f498e-121">Aracı kullanarak sorun buldıysanız, lütfen aracın [GitHub deposunda](https://github.com/dotnet/upgrade-assistant)bunları bildirin.</span><span class="sxs-lookup"><span data-stu-id="f498e-121">If you discover problems using the tool, please report them in the tool's [GitHub repository](https://github.com/dotnet/upgrade-assistant).</span></span>

## <a name="how-to-install-the-net-upgrade-assistant"></a><span data-ttu-id="f498e-122">.NET yükseltme yardımcısını nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="f498e-122">How to install the .NET Upgrade Assistant</span></span>

<span data-ttu-id="f498e-123">[Kullanmaya başlama öğreticisi](https://aka.ms/dotnet-upgrade-assistant-install) , .NET Yükseltme Yardımcısı 'nı nasıl yükleyip kullanacağınızı adım adım göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f498e-123">The [Get Started tutorial](https://aka.ms/dotnet-upgrade-assistant-install) walks through how to install and use the .NET Upgrade Assistant.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="f498e-124">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f498e-124">Prerequisites</span></span>

1. <span data-ttu-id="f498e-125">Bu araç proje dosyalarıyla çalışmak için MSBuild kullanır.</span><span class="sxs-lookup"><span data-stu-id="f498e-125">This tool uses MSBuild to work with project files.</span></span> <span data-ttu-id="f498e-126">MSBuild 'in son sürümünün yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f498e-126">Make sure that a recent version of MSBuild is installed.</span></span> <span data-ttu-id="f498e-127">Bunu yapmanın kolay bir yolu, [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)' i yüklemektir.</span><span class="sxs-lookup"><span data-stu-id="f498e-127">An easy way to do this is to [install Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).</span></span>
1. <span data-ttu-id="f498e-128">Bu araç [TRY-Convert 'e](https://github.com/dotnet/try-convert)bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="f498e-128">This tool depends on [try-convert](https://github.com/dotnet/try-convert).</span></span> <span data-ttu-id="f498e-129">Aracın doğru çalışması için, proje dosyalarını yeni SDK stiline dönüştürmek üzere TRY-Convert aracını yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f498e-129">In order for the tool to run correctly, you must install the try-convert tool for converting project files to the new SDK style.</span></span> <span data-ttu-id="f498e-130">Zaten bir **deneme** sürümüne sahipseniz, bunun yerine güncelleştirmeniz gerekebilir ( **yükseltmeden sonra Yükseltme Yardımcısı** _0.7.212201_ veya üzeri sürüme bağlıdır)</span><span class="sxs-lookup"><span data-stu-id="f498e-130">If you already have **try-convert** installed, you may need to update it instead (since **upgrade-assistant** depends on version _0.7.212201_ or later)</span></span>
    1. <span data-ttu-id="f498e-131">TRY-Convert ' i yüklemek için: `dotnet tool install -g try-convert`</span><span class="sxs-lookup"><span data-stu-id="f498e-131">To install try-convert: `dotnet tool install -g try-convert`</span></span>
    1. <span data-ttu-id="f498e-132">Güncelleştirmek için dene-Dönüştür: `dotnet tool update -g try-convert`</span><span class="sxs-lookup"><span data-stu-id="f498e-132">To update try-convert: `dotnet tool update -g try-convert`</span></span>

### <a name="installation-steps"></a><span data-ttu-id="f498e-133">Yükleme adımları</span><span class="sxs-lookup"><span data-stu-id="f498e-133">Installation steps</span></span>

<span data-ttu-id="f498e-134">Araç aşağıdakileri çalıştırarak bir .NET CLı aracı olarak yüklenebilir: `dotnet tool install -g upgrade-assistant --add-source https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet-tools/nuget/v3/index.json`</span><span class="sxs-lookup"><span data-stu-id="f498e-134">The tool can be installed as a .NET CLI tool by running: `dotnet tool install -g upgrade-assistant --add-source https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet-tools/nuget/v3/index.json`</span></span>

<span data-ttu-id="f498e-135">Benzer şekilde, .NET Yükseltme Yardımcısı bir .NET CLı aracı olarak yüklendiği için şu şekilde çalıştırılarak kolayca güncelleştirilebilirler: `https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet-tools/nuget/v3/index.json`</span><span class="sxs-lookup"><span data-stu-id="f498e-135">Similarly, because the .NET Upgrade Assistant is installed as a .NET CLI tool, it can be easily updated by running: `https://pkgs.dev.azure.com/dnceng/public/_packaging/dotnet-tools/nuget/v3/index.json`</span></span>

<span data-ttu-id="f498e-136">Ayrıntılı yükleme yönergeleri için lütfen projenin [Benioku](https://github.com/dotnet/upgrade-assistant)dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="f498e-136">For detailed installation instructions, please refer to the project's [README](https://github.com/dotnet/upgrade-assistant).</span></span>

## <a name="see-also"></a><span data-ttu-id="f498e-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f498e-137">See also</span></span>

- [<span data-ttu-id="f498e-138">.NET Yükseltme Yardımcısı ile bir WPF uygulamasını .NET 5 ' e yükseltme</span><span class="sxs-lookup"><span data-stu-id="f498e-138">Upgrade a WPF App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-wpf-framework.md)
- [<span data-ttu-id="f498e-139">.NET Yükseltme Yardımcısı ile bir Windows Forms uygulamasını .NET 5 ' e yükseltme</span><span class="sxs-lookup"><span data-stu-id="f498e-139">Upgrade a Windows Forms App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-winforms-framework.md)
- [<span data-ttu-id="f498e-140">.NET Yükseltme Yardımcısı ile bir ASP.NET MVC uygulamasını .NET 5 ' e yükseltme</span><span class="sxs-lookup"><span data-stu-id="f498e-140">Upgrade an ASP.NET MVC App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-aspnetmvc.md)
- [<span data-ttu-id="f498e-141">.NET Yükseltme Yardımcısı GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="f498e-141">.NET Upgrade Assistant GitHub Repository</span></span>](https://github.com/dotnet/upgrade-assistant)
