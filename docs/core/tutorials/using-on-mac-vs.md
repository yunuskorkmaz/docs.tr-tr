---
title: Mac için Visual Studio kullanarak .NET Core kullanmaya başlama
description: Bu konu, Mac için Visual Studio ve .NET Core'u kullanarak basit bir konsol uygulaması oluşturmanıza yol açabilirsiniz.
ms.date: 12/19/2019
ms.openlocfilehash: 4cd7e311411bce62698e291e763227496877ea39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740484"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="1abe2-103">Mac için Visual Studio kullanarak macOS üzerinde .NET Core kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="1abe2-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="1abe2-104">Mac için Visual Studio, .NET Core uygulamalarını geliştirmek için tam özellikli entegre geliştirme ortamı (IDE) sağlar.</span><span class="sxs-lookup"><span data-stu-id="1abe2-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="1abe2-105">Bu makale, Mac ve .NET Core için Visual Studio'yu kullanarak basit bir konsol uygulaması oluşturmanıza yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="1abe2-105">This article walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="1abe2-106">Geri bildiriminiz çok değerlidir.</span><span class="sxs-lookup"><span data-stu-id="1abe2-106">Your feedback is highly valued.</span></span> <span data-ttu-id="1abe2-107">Mac için Visual Studio'daki geliştirme ekibine geri bildirim sağlamanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="1abe2-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="1abe2-108">Mac için Visual Studio'da, menüden **Sorun Bildir'i** > **Report a Problem** veya hata raporu doldurmak için bir pencere açacak olan Karşılama ekranından Sorunu Bildir'i'ni seçin. **Report a Problem**</span><span class="sxs-lookup"><span data-stu-id="1abe2-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="1abe2-109">Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) portalında izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1abe2-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="1abe2-110">Öneride bulunmak için, menüden **Öneri Sağlama'ya Yardım Et'i** > **Provide a Suggestion** veya Sizi Mac Developer Community web sayfası için [Visual Studio'ya](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)götürecek olan Karşılama ekranından Bir **Öneri Sağlayın'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="1abe2-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1abe2-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1abe2-111">Prerequisites</span></span>

<span data-ttu-id="1abe2-112">[.NET Çekirdek bağımlılıkları ve gereksinimleri](../install/dependencies.md?pivots=os-macos) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="1abe2-112">See the [.NET Core dependencies and requirements](../install/dependencies.md?pivots=os-macos) article.</span></span>

<span data-ttu-id="1abe2-113">.NET Core'un desteklenen bir sürümünü kullandığınızdan emin olmak için [.NET Çekirdek Desteği](/visualstudio/mac/net-core-support) makalesini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="1abe2-113">Check the [.NET Core Support](/visualstudio/mac/net-core-support) article to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="1abe2-114">Başlarken</span><span class="sxs-lookup"><span data-stu-id="1abe2-114">Get started</span></span>

<span data-ttu-id="1abe2-115">Mac için ön koşulları ve Visual Studio'yu zaten yüklediyseniz, bu bölümü atlayın ve proje oluşturmaya devam [edin.](#creating-a-project)</span><span class="sxs-lookup"><span data-stu-id="1abe2-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="1abe2-116">Mac için ön koşulları ve Visual Studio'yu yüklemek için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="1abe2-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="1abe2-117">Mac [yükleyici için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)indirin.</span><span class="sxs-lookup"><span data-stu-id="1abe2-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="1abe2-118">Yükleyiciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1abe2-118">Run the installer.</span></span> <span data-ttu-id="1abe2-119">Lisans sözleşmesini okuyun ve kabul edin.</span><span class="sxs-lookup"><span data-stu-id="1abe2-119">Read and accept the license agreement.</span></span> <span data-ttu-id="1abe2-120">Yükleme sırasında .NET Core'u yükleme seçeneğini seçin.</span><span class="sxs-lookup"><span data-stu-id="1abe2-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="1abe2-121">Platformlar arası mobil uygulama geliştirme teknolojisi olan Xamarin'i yükleme fırsatı nasibini aldınız.</span><span class="sxs-lookup"><span data-stu-id="1abe2-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="1abe2-122">Xamarin ve ilgili bileşenlerinin yüklenmesi .NET Core geliştirme için isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1abe2-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="1abe2-123">Mac yükleme işlemi için Visual Studio'nun bir bölümü [için, Mac belgeleri için Visual Studio'ya](/visualstudio/mac/)bakın.</span><span class="sxs-lookup"><span data-stu-id="1abe2-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="1abe2-124">Yükleme tamamlandığında, Mac IDE için Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="1abe2-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="1abe2-125">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="1abe2-125">Creating a project</span></span>

1. <span data-ttu-id="1abe2-126">Başlangıç penceresinde **Yeni'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="1abe2-126">Select **New** on the start window.</span></span>

   ![Mac Başlangıç ekranı için Visual Studio'da yeni düğme](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="1abe2-128">Yeni **Proje** iletişim kutusunda,.NET **Core** düğümünün altındaki **Uygulamayı** seçin.</span><span class="sxs-lookup"><span data-stu-id="1abe2-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="1abe2-129">Konsol **Uygulaması** şablonu ve ardından **Next'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="1abe2-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![Yeni proje şablonları listesi](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="1abe2-131">.NET Core'un birden fazla sürümü yüklüyse, projeniz için hedef çerçeveyi seçin.</span><span class="sxs-lookup"><span data-stu-id="1abe2-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="1abe2-132">**Proje Adı**için "HelloWorld" yazın.</span><span class="sxs-lookup"><span data-stu-id="1abe2-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="1abe2-133">**Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="1abe2-133">Select **Create**.</span></span>

   ![Yeni Konsol Uygulaması iletişim günlüğüne yapıla](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="1abe2-135">Projenin bağımlılıkları geri yüklenirken bekleyin.</span><span class="sxs-lookup"><span data-stu-id="1abe2-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="1abe2-136">Proje, *Program.cs,* bir yönteme sahip `Program` bir sınıf `Main` içeren tek bir C# dosyasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1abe2-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="1abe2-137">Açıklamada `Console.WriteLine` "Merhaba Dünya!" çıkacaktır.</span><span class="sxs-lookup"><span data-stu-id="1abe2-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="1abe2-138">uygulama çalıştırıldığında konsola.</span><span class="sxs-lookup"><span data-stu-id="1abe2-138">to the console when the app is run.</span></span>

   ![Program.cs dosyaaçık ana pencere](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="1abe2-140">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1abe2-140">Run the application</span></span>

<span data-ttu-id="1abe2-141">Uygulamayı Hata Ayıklama modunda (komut + enter) kullanarak veya Sürüm modunda (seçenek + komut + girin) kullanarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1abe2-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![Uygulama Çıktı sı, Hello World'u gösteriyor!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="1abe2-143">Sonraki adım</span><span class="sxs-lookup"><span data-stu-id="1abe2-143">Next step</span></span>

<span data-ttu-id="1abe2-144">Mac konusu [için Visual Studio'yu kullanarak macOS'ta eksiksiz bir .NET Core çözümü oluşturma,](using-on-mac-vs-full-solution.md) yeniden kullanılabilir bir kitaplık ve birim testi içeren eksiksiz bir .NET Core çözüm oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1abe2-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
