---
title: Mac için Visual Studio kullanarak macOS üzerinde .NET Core kullanmaya başlama
description: Bu konu başlığı altında Mac ve .NET Core için Visual Studio kullanarak basit bir konsol uygulaması oluşturma sürecinde size yol gösterir.
author: mairaw
ms.date: 06/12/2017
ms.custom: seodec18
ms.openlocfilehash: 4467842c0b65ea536cc26601981d9fcc2bc68f2d
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300045"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="c2f1f-103">Mac için Visual Studio kullanarak macOS üzerinde .NET Core kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="c2f1f-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="c2f1f-104">Mac için Visual Studio, .NET Core uygulamaları geliştirmek için bir tam özellikli tümleşik geliştirme ortamı (IDE) sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="c2f1f-105">Bu konu başlığı altında Mac ve .NET Core için Visual Studio kullanarak basit bir konsol uygulaması oluşturma sürecinde size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="c2f1f-106">Geri bildiriminiz çok değerli.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-106">Your feedback is highly valued.</span></span> <span data-ttu-id="c2f1f-107">Mac için Visual Studio geliştirme ekibine geri bildirim sağlayabilirsiniz iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="c2f1f-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="c2f1f-108">Mac için Visual Studio'da **yardımcı** > **sorun bildir** menüsünden veya **sorun bildir** Karşılama ekranında, bir pencere açılır bir hata raporu dosyalama.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="c2f1f-109">Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) portalında izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="c2f1f-110">Bir öneride bulunmak için seçin **yardımcı** > **bir öneride** menüsünden veya **bir öneride** Karşılama ekranında, hangi yönlendirilirsiniz için [Mac Geliştirici topluluğu Web sayfası için visual Studio](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="c2f1f-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c2f1f-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c2f1f-111">Prerequisites</span></span>

<span data-ttu-id="c2f1f-112">Bkz: [Mac üzerinde .NET Core önkoşulları](../../core/macos-prerequisites.md) konu.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-112">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

## <a name="get-started"></a><span data-ttu-id="c2f1f-113">Kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="c2f1f-113">Get started</span></span>

<span data-ttu-id="c2f1f-114">Mac için Visual Studio ve önkoşullar önce yüklediğiniz, bu bölümü atlayarak devam [proje oluşturma](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="c2f1f-114">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="c2f1f-115">Mac için Visual Studio ve önkoşulları yüklemek için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="c2f1f-115">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="c2f1f-116">İndirme [yükleyicisi Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="c2f1f-116">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="c2f1f-117">Yükleyiciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-117">Run the installer.</span></span> <span data-ttu-id="c2f1f-118">Okuyun ve lisans sözleşmesini kabul edin.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-118">Read and accept the license agreement.</span></span> <span data-ttu-id="c2f1f-119">Yükleme sırasında Xamarin, platformlar arası mobil uygulama geliştirme teknolojisinden yüklemek için bir fırsat sunulur.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-119">During the install, you're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="c2f1f-120">Xamarin ve ilgili bileşenlerini yüklemek için .NET Core geliştirme isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-120">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="c2f1f-121">Yükleme işlemi Mac için Visual Studio ile ilgili kılavuz için bkz: [belgeleri Mac için Visual Studio](/visualstudio/mac/).</span><span class="sxs-lookup"><span data-stu-id="c2f1f-121">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="c2f1f-122">Yükleme tamamlandığında, Mac IDE için Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-122">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="c2f1f-123">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="c2f1f-123">Creating a project</span></span>

1. <span data-ttu-id="c2f1f-124">Seçin **yeni proje** Hoş Geldiniz ekranında.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-124">Select **New Project** on the Welcome screen.</span></span>

   ![Yeni Proje düğmesi Visual Studio Mac Hoş Geldiniz ekranı](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="c2f1f-126">İçinde **yeni proje** iletişim kutusunda **uygulama** altında **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-126">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="c2f1f-127">Seçin **konsol uygulaması** şablonu ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-127">Select the **Console Application** template followed by **Next**.</span></span>

   ![Yeni proje şablonları listesi](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="c2f1f-129">"HelloWorld" türü **proje adı**.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-129">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="c2f1f-130">**Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-130">Select **Create**.</span></span>

   ![Yeni konsol uygulaması iletişim kutusu yapılandırın](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="c2f1f-132">Proje bağımlılıklarınızı geri yüklerken bekleyin.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-132">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="c2f1f-133">Tek bir projeye sahip C# dosyası *Program.cs*, kapsayan bir `Program` sınıfıyla birlikte bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-133">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="c2f1f-134">`Console.WriteLine` Deyimi "Hello World!" çıkış</span><span class="sxs-lookup"><span data-stu-id="c2f1f-134">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="c2f1f-135">Uygulamayı çalıştırdığınızda konsola.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-135">to the console when the app is run.</span></span>

   ![Program.cs dosyasının ana penceresi açın](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="c2f1f-137">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c2f1f-137">Run the application</span></span>

<span data-ttu-id="c2f1f-138">Uygulamayı hata ayıklama moduyla çalıştırma <kbd>F5</kbd> veya sürüm modu kullanarak <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-138">Run the app in Debug mode using <kbd>F5</kbd> or in Release mode using <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>

![Uygulama çıkış Bölmesi ' Hello World gösterir!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="c2f1f-140">Sonraki adım</span><span class="sxs-lookup"><span data-stu-id="c2f1f-140">Next step</span></span>

<span data-ttu-id="c2f1f-141">[Mac için Visual Studio kullanarak macos'ta eksiksiz bir .NET Core çözümü derleme](using-on-mac-vs-full-solution.md) konu, bir yeniden kullanılabilir bir kitaplık ve birim testi içeren eksiksiz bir .NET Core çözümü derleme nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2f1f-141">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
