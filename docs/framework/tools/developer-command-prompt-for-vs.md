---
title: Visual Studio için Geliştirici Komut Komut Ustem
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: f028281d477284acf3ac4dac63f5ddbbd79f5259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715827"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="4697a-102">Visual Studio için Geliştirici Komut Komut Ustem</span><span class="sxs-lookup"><span data-stu-id="4697a-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="4697a-103">Visual Studio için Geliştirici Komut Komut Ustem ,.NET Framework araçlarını daha kolay kullanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4697a-103">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="4697a-104">Belirli ortam değişkenlerini otomatik olarak ayarlayan bir komut istemidir.</span><span class="sxs-lookup"><span data-stu-id="4697a-104">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="4697a-105">Geliştirici Komut Komut Ustem'i açtıktan sonra [.NET](index.md) `ildasm` Framework `clrver`araçları nın komutlarını girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4697a-105">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4697a-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4697a-106">Prerequisites</span></span>

- [<span data-ttu-id="4697a-107">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="4697a-107">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="4697a-108">Makinenizde komut istemini arama</span><span class="sxs-lookup"><span data-stu-id="4697a-108">Search for the command prompt on your machine</span></span>

<span data-ttu-id="4697a-109">Visual Studio'nun sürümüne ve yüklediğiniz ek SDK'lara ve iş yüklerine bağlı olarak birden çok komut isteminiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="4697a-109">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="4697a-110">Aşağıdaki adımlar işe yaramazsa, [makinenizdeki dosyaları el ile bulmaya](#manually-locate-the-files-on-your-machine) çalışabilir veya Visual [Studio'nun içinden komut istemini başlatabilirsiniz.](#start-the-command-prompt-from-inside-visual-studio)</span><span class="sxs-lookup"><span data-stu-id="4697a-110">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="4697a-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="4697a-111">Windows 10</span></span>

1. <span data-ttu-id="4697a-112">Klavyede Windows logotutu **başlat'ı** ![seçin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="4697a-112">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="4697a-113">ve **V**harfine kaydırın.</span><span class="sxs-lookup"><span data-stu-id="4697a-113">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="4697a-114">Visual **Studio 2019** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="4697a-114">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="4697a-115">**VS 2019 için Geliştirici Komut Komut Ustem'i** (veya kullanmak istediğiniz komut istemini) seçin.</span><span class="sxs-lookup"><span data-stu-id="4697a-115">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="4697a-116">Alternatif olarak, görev çubuğundaki arama kutusuna komut isteminin adını yazmaya başlayabilir ve sonuç listesi arama eşleşmelerini görüntülemeye başladığında istediğiniz sonucu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4697a-116">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![Windows 10'daki arama davranışını gösteren animasyonlu gif](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="4697a-118">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="4697a-118">Windows 8.1</span></span>

1. <span data-ttu-id="4697a-119">Klavyedeki **Start** Windows logosu tuşu ![Windows logo tuşuna basarak Başlangıç ekranına gidin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="4697a-119">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="4697a-120">örneğin klavyenizde.</span><span class="sxs-lookup"><span data-stu-id="4697a-120">on your keyboard for example.</span></span>

1. <span data-ttu-id="4697a-121">**Başlangıç** ekranında, **Uygulamalar** listesini açmak için **Ctrl**+**Sekmesine** basın ve ardından **V**tuşuna basın. Bu, yüklenen tüm Visual Studio komut istemlerini içeren bir liste getirir.</span><span class="sxs-lookup"><span data-stu-id="4697a-121">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="4697a-122">**VS 2019 için Geliştirici Komut Komut Ustem'i** (veya kullanmak istediğiniz komut istemini) seçin.</span><span class="sxs-lookup"><span data-stu-id="4697a-122">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="4697a-123">Windows 7</span><span class="sxs-lookup"><span data-stu-id="4697a-123">Windows 7</span></span>

1. <span data-ttu-id="4697a-124">**Başlat'ı** seçin ve ardından **Tüm Programları**genişletin.</span><span class="sxs-lookup"><span data-stu-id="4697a-124">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="4697a-125">**VS 2019 için**Visual Studio **2019** > Visual Studio**Tools** > Developer Command Prompt'ı veya kullanmak istediğiniz komut istemini seçin.</span><span class="sxs-lookup"><span data-stu-id="4697a-125">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![Komut istemi vurgulanan Windows 7 Başlat menüsü](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="4697a-127">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümler](https://developer.microsoft.com/windows/downloads/sdk-archive)gibi yüklü başka SDK'lar varsa, ek komut istemleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4697a-127">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="4697a-128">Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="4697a-128">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="4697a-129">Makinenizdeki dosyaları el ile bulma</span><span class="sxs-lookup"><span data-stu-id="4697a-129">Manually locate the files on your machine</span></span>

<span data-ttu-id="4697a-130">Genellikle, yüklediğiniz komut istemleri için kısayollar Visual Studio için **Başlat Menüsü** klasörüne yerleştirilir( örneğin *ProgramData%\Microsoft\Windows\Başlat Menüsü\Programlar\Visual Studio 2019\Visual Studio Tools.*</span><span class="sxs-lookup"><span data-stu-id="4697a-130">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="4697a-131">Ancak, nedense komut istemini aramak beklenen sonuçları üretmiyorsa, makinenizdeki kısayolu el ile bulmaya çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4697a-131">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="4697a-132">*VsDevCmd.bat*gibi komut istemi dosyasının adını aramayı deneyin veya *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (Visual Studio sürümünüze, sürüme ve yükleme konumunuza göre yol değişiklikleri) gibi Araçlar klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="4697a-132">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="4697a-133">Visual Studio'nun içinden komut istemini başlatın</span><span class="sxs-lookup"><span data-stu-id="4697a-133">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="4697a-134">Daha kolay erişim için Visual Studio'daki Araçlar menüsüne Geliştirici Komut Komut Ustem'i veya başka bir komut istemi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4697a-134">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="4697a-135">Aracı kullanılabilir hale getirmek için dış araçlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4697a-135">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="4697a-136">Adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="4697a-136">Here are the steps:</span></span>

1. <span data-ttu-id="4697a-137">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="4697a-137">Open Visual Studio.</span></span>

1. <span data-ttu-id="4697a-138">Başlangıç penceresinde, **kodsuz Devam**et'i seçin.</span><span class="sxs-lookup"><span data-stu-id="4697a-138">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="4697a-139">Menü çubuğunda **Araçlar** > **Dış Araçlar'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="4697a-139">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="4697a-140">Dış **Araçlar** iletişim kutusunda **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="4697a-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="4697a-141">Yeni bir giriş görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4697a-141">A new entry appears.</span></span>

1. <span data-ttu-id="4697a-142">Yeni menü öğeniz **için** başlık `Command Prompt`girin.</span><span class="sxs-lookup"><span data-stu-id="4697a-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="4697a-143">**Komut** alanında, başlatmak istediğiniz dosyayı belirtin, `%comspec%` `C:\Windows\System32\cmd.exe`örneğin .</span><span class="sxs-lookup"><span data-stu-id="4697a-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="4697a-144">**Bağımsızlar** alanında, kullanmak istediğiniz komut istemini nerede bulacağınıbelirtin. `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`</span><span class="sxs-lookup"><span data-stu-id="4697a-144">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="4697a-145">Bu komut Visual Studio 2019 Topluluğu ile yüklenen Geliştirici Komut Komut Komut Ustem'i başlatın.</span><span class="sxs-lookup"><span data-stu-id="4697a-145">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="4697a-146">Bu değeri Visual Studio sürümünüze, sürümünüze ve yükleme konumunuza göre değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4697a-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="4697a-147">İlk **dizin** alanında, komut isteminin başlatılacacağı dizini belirtin.</span><span class="sxs-lookup"><span data-stu-id="4697a-147">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="4697a-148">Alanın yanındaki oku seçerek **Proje Dizini** gibi bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="4697a-148">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="4697a-149">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="4697a-149">Choose the **OK** button.</span></span>

   ![Dış Araçlar, doldurulan alan değerleriyle iletişim ilerler.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="4697a-151">Yeni menü öğesi eklenir ve Araçlar menüsünden komut istemine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4697a-151">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Visual Studio'da komut istemi menü öğesi](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="4697a-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4697a-153">See also</span></span>

- [<span data-ttu-id="4697a-154">.NET Framework Araçları</span><span class="sxs-lookup"><span data-stu-id="4697a-154">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="4697a-155">Dış Araçları Yönetme</span><span class="sxs-lookup"><span data-stu-id="4697a-155">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="4697a-156">Komut satırından Microsoft C++ araç kümesini kullanma</span><span class="sxs-lookup"><span data-stu-id="4697a-156">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
