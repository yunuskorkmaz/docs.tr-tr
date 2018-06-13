---
title: Mac için Visual Studio kullanarak macOS üzerinde .NET Core'u kullanmaya başlama
description: Bu konu, Mac ve .NET Core için Visual Studio kullanarak basit bir konsol uygulaması oluşturma sürecinde açıklanmaktadır.
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.openlocfilehash: 82cd7c09dd595a8273eb88a4caaf34782fa10ac4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214549"
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="4fd8a-103">Mac için Visual Studio kullanarak macOS üzerinde .NET Core'u kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="4fd8a-103">Getting started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="4fd8a-104">Mac için Visual Studio .NET Core uygulamaları geliştirmek için bir tam özellikli tümleşik geliştirme ortamı (IDE) sağlar.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="4fd8a-105">Bu konu, Mac ve .NET Core için Visual Studio kullanarak basit bir konsol uygulaması oluşturma sürecinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="4fd8a-106">Geri bildiriminiz yüksek değerli.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-106">Your feedback is highly valued.</span></span> <span data-ttu-id="4fd8a-107">Mac için Visual Studio geliştirme ekibine geribildirim sağlayabilir iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="4fd8a-107">There are a two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="4fd8a-108">Mac için Visual Studio'da seçin **yardımcı** > **bir sorun bildirmek** menüsünden veya **bir sorun bildirmek** Karşılama ekranında olduğu için bir pencere açılır bir hata raporu dosyalama.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="4fd8a-109">Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) portalında izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="4fd8a-110">Bir öneride bulunmak için seçin **yardımcı** > **bir öneride bulunmak** menüsünden veya **bir öneride bulunmak** Karşılama ekranında, hangi yönlendirilirsiniz için [Mac UserVoice Web sayfası için visual Studio](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span><span class="sxs-lookup"><span data-stu-id="4fd8a-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac UserVoice webpage](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4fd8a-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4fd8a-111">Prerequisites</span></span>

<span data-ttu-id="4fd8a-112">Bkz: [.NET Core Mac üzerinde önkoşulları](../../core/macos-prerequisites.md) konu.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-112">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

## <a name="getting-started"></a><span data-ttu-id="4fd8a-113">Başlarken</span><span class="sxs-lookup"><span data-stu-id="4fd8a-113">Getting started</span></span>

<span data-ttu-id="4fd8a-114">Mac için Önkoşullar ve Visual Studio zaten yüklediniz, bu bölüm atlayın ve devam [proje oluşturma](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="4fd8a-114">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="4fd8a-115">Mac için Visual Studio ve önkoşulları yüklemek için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="4fd8a-115">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="4fd8a-116">Karşıdan [Mac Yükleyicisi için Visual Studio](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="4fd8a-116">Download the [Visual Studio for Mac installer](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> <span data-ttu-id="4fd8a-117">Yükleyiciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-117">Run the installer.</span></span> <span data-ttu-id="4fd8a-118">Okuyun ve Lisans Sözleşmesi'ni kabul edin.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-118">Read and accept the license agreement.</span></span> <span data-ttu-id="4fd8a-119">Yükleme sırasında Xamarin, platformlar arası mobil uygulama geliştirme teknolojisi yükleme fırsatı sağlanan.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-119">During the install, you're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="4fd8a-120">Xamarin ve ilgili bileşenlerini yüklemek için .NET Core geliştirme isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-120">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="4fd8a-121">Visual Studio Mac yükleme işlemi için kılavuz için bkz: [Mac için Visual Studio Tanıtımı](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="4fd8a-121">For a walk-through of the Visual Studio for Mac install process, see [Introducing Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span></span> <span data-ttu-id="4fd8a-122">Yükleme tamamlandığında, Mac IDE için Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-122">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="4fd8a-123">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="4fd8a-123">Creating a project</span></span>

1. <span data-ttu-id="4fd8a-124">Seçin **yeni proje** Hoş Geldiniz ekranında.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-124">Select **New Project** on the Welcome screen.</span></span>

   ![Mac Hoş Geldiniz ekranı için Visual Studio yeni proje düğmesinde](./media/using-on-mac-vs/vsmac1.png)

1. <span data-ttu-id="4fd8a-126">İçinde **yeni proje** iletişim kutusunda **uygulama** altında **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-126">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="4fd8a-127">Seçin **konsol uygulaması** şablonu ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-127">Select the **Console Application** template followed by **Next**.</span></span>

   ![Yeni proje şablonları listesi](./media/using-on-mac-vs/vsmac2.png)

1. <span data-ttu-id="4fd8a-129">"HelloWorld" türü **proje adı**.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-129">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="4fd8a-130">Seçin **oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-130">Select **Create**.</span></span>

   ![Yeni konsol uygulaması iletişim yapılandırın](./media/using-on-mac-vs/vsmac3.png)

1. <span data-ttu-id="4fd8a-132">Proje bağımlılıkları geri bekleyin.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-132">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="4fd8a-133">Tek bir C# dosyası, projenin içerdiğinden *Program.cs*, içeren bir `Program` ile sınıf bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-133">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="4fd8a-134">`Console.WriteLine` Deyimi "Hello World!" çıktı</span><span class="sxs-lookup"><span data-stu-id="4fd8a-134">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="4fd8a-135">Uygulama çalıştırıldığında konsola.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-135">to the console when the app is run.</span></span>

   ![Program.cs dosyasını ana penceresi açın](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a><span data-ttu-id="4fd8a-137">Uygulamayı çalıştırın</span><span class="sxs-lookup"><span data-stu-id="4fd8a-137">Run the application</span></span>

<span data-ttu-id="4fd8a-138">Hata ayıklama modunu kullanarak uygulama çalıştırma <kbd>F5</kbd> veya yayın modunu kullanarak <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-138">Run the app in Debug mode using <kbd>F5</kbd> or in Release mode using <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>

![Uygulama çıkış Bölmesi ' Hello World gösterir!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a><span data-ttu-id="4fd8a-140">Sonraki adım</span><span class="sxs-lookup"><span data-stu-id="4fd8a-140">Next step</span></span>

<span data-ttu-id="4fd8a-141">[Mac için Visual Studio kullanarak macOS üzerinde eksiksiz bir .NET Core çözümü derleme](using-on-mac-vs-full-solution.md) konu yeniden kullanılabilir kitaplık ve birim testi içeren tam bir .NET Core çözümünü nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4fd8a-141">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
