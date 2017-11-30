---
title: "Mac için Visual Studio kullanarak macOS üzerinde .NET Core'u kullanmaya başlama"
description: "Bu konu, Mac ve .NET Core için Visual Studio kullanarak basit bir konsol uygulaması oluşturma sürecinde açıklanmaktadır."
keywords: .NET, .NET core macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8902e849-dd17-42c0-8264-cc7ae3927a0c
ms.openlocfilehash: 893999f9abcc299da4fb0923fe47c371079f695c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="be58f-104">Mac için Visual Studio kullanarak macOS üzerinde .NET Core'u kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="be58f-104">Getting started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="be58f-105">Mac için Visual Studio .NET Core uygulamaları geliştirmek için bir tam özellikli tümleşik geliştirme ortamı (IDE) sağlar.</span><span class="sxs-lookup"><span data-stu-id="be58f-105">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="be58f-106">Bu konu, Mac ve .NET Core için Visual Studio kullanarak basit bir konsol uygulaması oluşturma sürecinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="be58f-106">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="be58f-107">Geri bildiriminiz yüksek değerli.</span><span class="sxs-lookup"><span data-stu-id="be58f-107">Your feedback is highly valued.</span></span> <span data-ttu-id="be58f-108">Mac için Visual Studio geliştirme ekibine geribildirim sağlayabilir iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="be58f-108">There are a two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="be58f-109">Mac için Visual Studio'da seçin **yardımcı** > **bir sorun bildirmek** menüsünden veya **bir sorun bildirmek** Karşılama ekranında olduğu için bir pencere açılır bir hata raporu dosyalama.</span><span class="sxs-lookup"><span data-stu-id="be58f-109">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="be58f-110">Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) portalında izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be58f-110">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="be58f-111">Bir öneride bulunmak için seçin **yardımcı** > **bir öneride bulunmak** menüsünden veya **bir öneride bulunmak** Karşılama ekranında, hangi yönlendirilirsiniz için [Mac UserVoice Web sayfası için visual Studio](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span><span class="sxs-lookup"><span data-stu-id="be58f-111">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac UserVoice webpage](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be58f-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="be58f-112">Prerequisites</span></span>

<span data-ttu-id="be58f-113">Bkz: [.NET Core Mac üzerinde önkoşulları](../../core/macos-prerequisites.md) konu.</span><span class="sxs-lookup"><span data-stu-id="be58f-113">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

## <a name="getting-started"></a><span data-ttu-id="be58f-114">Başlarken</span><span class="sxs-lookup"><span data-stu-id="be58f-114">Getting started</span></span>

<span data-ttu-id="be58f-115">Mac için Önkoşullar ve Visual Studio zaten yüklediniz, bu bölüm atlayın ve devam [proje oluşturma](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="be58f-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="be58f-116">Mac için Visual Studio ve önkoşulları yüklemek için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="be58f-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="be58f-117">Karşıdan [Mac Yükleyicisi için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="be58f-117">Download the [Visual Studio for Mac installer](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> <span data-ttu-id="be58f-118">Yükleyiciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="be58f-118">Run the installer.</span></span> <span data-ttu-id="be58f-119">Okuyun ve Lisans Sözleşmesi'ni kabul edin.</span><span class="sxs-lookup"><span data-stu-id="be58f-119">Read and accept the license agreement.</span></span> <span data-ttu-id="be58f-120">Yükleme sırasında Xamarin, platformlar arası mobil uygulama geliştirme teknolojisi yükleme fırsatı sağlanan.</span><span class="sxs-lookup"><span data-stu-id="be58f-120">During the install, you're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="be58f-121">Xamarin ve ilgili bileşenlerini yüklemek için .NET Core geliştirme isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="be58f-121">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="be58f-122">Visual Studio Mac yükleme işlemi için kılavuz için bkz: [Mac için Visual Studio Tanıtımı](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="be58f-122">For a walk-through of the Visual Studio for Mac install process, see [Introducing Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span></span> <span data-ttu-id="be58f-123">Yükleme tamamlandığında, Mac IDE için Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="be58f-123">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="be58f-124">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="be58f-124">Creating a project</span></span>

1. <span data-ttu-id="be58f-125">Seçin **yeni proje** Hoş Geldiniz ekranında.</span><span class="sxs-lookup"><span data-stu-id="be58f-125">Select **New Project** on the Welcome screen.</span></span>

   ![Mac Hoş Geldiniz ekranı için Visual Studio yeni proje düğmesinde](./media/using-on-mac-vs/vsmac1.png)

1. <span data-ttu-id="be58f-127">İçinde **yeni proje** iletişim kutusunda **uygulama** altında **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="be58f-127">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="be58f-128">Seçin **konsol uygulaması** şablonu ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="be58f-128">Select the **Console Application** template followed by **Next**.</span></span>

   ![Yeni proje şablonları listesi](./media/using-on-mac-vs/vsmac2.png)

1. <span data-ttu-id="be58f-130">"HelloWorld" türü **proje adı**.</span><span class="sxs-lookup"><span data-stu-id="be58f-130">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="be58f-131">Seçin **oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="be58f-131">Select **Create**.</span></span>

   ![Yeni konsol uygulaması iletişim yapılandırın](./media/using-on-mac-vs/vsmac3.png)

1. <span data-ttu-id="be58f-133">Proje bağımlılıkları geri bekleyin.</span><span class="sxs-lookup"><span data-stu-id="be58f-133">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="be58f-134">Tek bir C# dosyası, projenin içerdiğinden *Program.cs*, içeren bir `Program` ile sınıf bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="be58f-134">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="be58f-135">`Console.WriteLine` Deyimi "Hello World!" çıktı</span><span class="sxs-lookup"><span data-stu-id="be58f-135">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="be58f-136">Uygulama çalıştırıldığında konsola.</span><span class="sxs-lookup"><span data-stu-id="be58f-136">to the console when the app is run.</span></span>

   ![Program.cs dosyasını ana penceresi açın](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a><span data-ttu-id="be58f-138">Uygulamayı çalıştırın</span><span class="sxs-lookup"><span data-stu-id="be58f-138">Run the application</span></span>

<span data-ttu-id="be58f-139">Hata ayıklama modunu kullanarak uygulama çalıştırma <kbd>F5</kbd> veya yayın modunu kullanarak <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="be58f-139">Run the app in Debug mode using <kbd>F5</kbd> or in Release mode using <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>

![Uygulama çıkış Bölmesi ' Hello World gösterir!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a><span data-ttu-id="be58f-141">Sonraki adım</span><span class="sxs-lookup"><span data-stu-id="be58f-141">Next step</span></span>

<span data-ttu-id="be58f-142">[Mac için Visual Studio kullanarak macOS üzerinde eksiksiz bir .NET Core çözümü derleme](using-on-mac-vs-full-solution.md) konu yeniden kullanılabilir kitaplık ve birim testi içeren tam bir .NET Core çözümünü nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="be58f-142">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
