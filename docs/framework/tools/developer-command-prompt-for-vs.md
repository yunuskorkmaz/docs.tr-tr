---
title: Visual Studio için Geliştirici Komut İstemi
description: .NET araçlarını daha kolay kullanmanıza imkan tanıyan Visual Studio için Geliştirici Komut İstemi kullanmayı öğrenin. Belirli ortam değişkenlerini otomatik olarak ayarlar.
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
ms.openlocfilehash: 92416820f47cb778dfcc916b8626df4aa328814c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167175"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="550e2-104">Visual Studio için Geliştirici Komut İstemi</span><span class="sxs-lookup"><span data-stu-id="550e2-104">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="550e2-105">Visual Studio için Geliştirici Komut İstemi, .NET Framework araçları daha kolay kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="550e2-105">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="550e2-106">Bu, belirli ortam değişkenlerini otomatik olarak ayarlayan bir komut istemi.</span><span class="sxs-lookup"><span data-stu-id="550e2-106">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="550e2-107">Geliştirici Komut İstemi açtıktan sonra, veya gibi [.NET Framework araçlara](index.md) yönelik komutları girebilirsiniz `ildasm` `clrver` .</span><span class="sxs-lookup"><span data-stu-id="550e2-107">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="550e2-108">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="550e2-108">Prerequisites</span></span>

- [<span data-ttu-id="550e2-109">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="550e2-109">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="550e2-110">Makinenizde komut istemi araması yapın</span><span class="sxs-lookup"><span data-stu-id="550e2-110">Search for the command prompt on your machine</span></span>

<span data-ttu-id="550e2-111">Visual Studio sürümüne ve yüklediğiniz ek SDK ve iş yüklerine bağlı olarak birden çok komut istemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="550e2-111">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="550e2-112">Aşağıdaki adımlar çalışmazsa, [makinenizde dosyaları el ile bulmayı](#manually-locate-the-files-on-your-machine) deneyebilir veya [komut Istemi 'Ni Visual Studio 'nun içinden başlatabilirsiniz](#start-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="550e2-112">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="550e2-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="550e2-113">Windows 10</span></span>

1. <span data-ttu-id="550e2-114">**Start** ![ Klavyede Windows logo tuşunu Başlat ' ı seçin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="550e2-114">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="550e2-115">ve **V**harfine kaydırın.</span><span class="sxs-lookup"><span data-stu-id="550e2-115">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="550e2-116">**Visual Studio 2019** klasörünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="550e2-116">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="550e2-117">VS 2019 (veya kullanmak istediğiniz komut istemi) **için geliştirici komut istemi** seçin.</span><span class="sxs-lookup"><span data-stu-id="550e2-117">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="550e2-118">Alternatif olarak, görev çubuğundaki arama kutusuna komut isteminin adını yazmaya başlayabilir ve sonuç listesi arama eşleşmelerini görüntülemeye başladıktan sonra istediğiniz sonucu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="550e2-118">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![Windows 10 ' da arama davranışını gösteren animasyonlu GIF](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="550e2-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="550e2-120">Windows 8.1</span></span>

1. <span data-ttu-id="550e2-121">Klavyede Windows logosu tuşu Windows logosu tuşuna basarak **Başlangıç** ekranına gidin ![ .](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="550e2-121">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="550e2-122">Örneğin, klavyenizde.</span><span class="sxs-lookup"><span data-stu-id="550e2-122">on your keyboard for example.</span></span>

1. <span data-ttu-id="550e2-123">**Başlat** ekranında, CTRL tuşuna basarak **Ctrl** + **Tab** **uygulamalar** listesini açın ve ardından **V**tuşuna basın. Bu, tüm yüklü Visual Studio komut istemlerini içeren bir liste görüntüler.</span><span class="sxs-lookup"><span data-stu-id="550e2-123">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="550e2-124">VS 2019 (veya kullanmak istediğiniz komut istemi) **için geliştirici komut istemi** seçin.</span><span class="sxs-lookup"><span data-stu-id="550e2-124">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="550e2-125">Windows 7</span><span class="sxs-lookup"><span data-stu-id="550e2-125">Windows 7</span></span>

1. <span data-ttu-id="550e2-126">**Başlat** ' ı ve ardından **tüm programlar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="550e2-126">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="550e2-127">VS 2019 için **Visual Studio 2019**  >  **Visual Studio Araçları**  >  **Geliştirici komut istemi**veya kullanmak istediğiniz komut istemi ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="550e2-127">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![Komut istemi vurgulanmış olarak Windows 7 Başlat menüsü](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="550e2-129">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümler](https://developer.microsoft.com/windows/downloads/sdk-archive)gibi başka SDK 'lar yüklüyse, ek komut istemleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="550e2-129">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="550e2-130">Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="550e2-130">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="550e2-131">Makinenizde dosyaları el ile bulun</span><span class="sxs-lookup"><span data-stu-id="550e2-131">Manually locate the files on your machine</span></span>

<span data-ttu-id="550e2-132">Genellikle, yüklediğiniz komut istemlerinin kısayolları, *% ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Araçları*gibi Visual Studio Için **Başlat menüsü** klasörüne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="550e2-132">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="550e2-133">Ancak, bazı nedenlerle komut istemi araması beklenen sonuçları oluşturmazsa, bu kısayolu makinenizde el ile bulmayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="550e2-133">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="550e2-134">*VsDevCmd.bat*gibi komut istemi dosyasının adını aramayı deneyin veya *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (Visual Studio sürümünüz, sürüm ve yükleme konumunuza göre yol değişiklikleri) gibi Araçlar klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="550e2-134">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="550e2-135">Komut istemi 'ni Visual Studio 'Nun içinden başlatın</span><span class="sxs-lookup"><span data-stu-id="550e2-135">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="550e2-136">Daha kolay erişim için, Visual Studio 'daki Araçlar menüsüne Geliştirici Komut İstemi veya başka bir komut istemi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="550e2-136">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="550e2-137">Aracı kullanılabilir hale getirmek için dış araçlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="550e2-137">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="550e2-138">Adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="550e2-138">Here are the steps:</span></span>

1. <span data-ttu-id="550e2-139">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="550e2-139">Open Visual Studio.</span></span>

1. <span data-ttu-id="550e2-140">Başlangıç penceresinde, **kod olmadan devam et**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="550e2-140">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="550e2-141">Menü çubuğunda **Araçlar**  >  **dış araçlar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="550e2-141">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="550e2-142">**Dış araçlar** Iletişim kutusunda **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="550e2-142">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="550e2-143">Yeni bir giriş görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="550e2-143">A new entry appears.</span></span>

1. <span data-ttu-id="550e2-144">Yeni menü öğesi için gibi bir **başlık** girin `Command Prompt` .</span><span class="sxs-lookup"><span data-stu-id="550e2-144">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="550e2-145">**Komut** alanında, başlatmak istediğiniz dosyayı (veya gibi) belirtin `%comspec%` `C:\Windows\System32\cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="550e2-145">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="550e2-146">**Bağımsız değişkenler** alanında, kullanmak istediğiniz belirli komut isteminin nerede bulunacağını belirtin, örneğin `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"` .</span><span class="sxs-lookup"><span data-stu-id="550e2-146">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="550e2-147">Bu komut, Visual Studio 2019 topluluğuyla yüklenmiş Geliştirici Komut İstemi başlatır.</span><span class="sxs-lookup"><span data-stu-id="550e2-147">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="550e2-148">Bu değeri, Visual Studio sürümünüz, sürümünüz ve yükleme konumunuza göre değiştirin.</span><span class="sxs-lookup"><span data-stu-id="550e2-148">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="550e2-149">**İlk dizin** alanında, komut istemi 'nin başlayacağı dizini belirtin.</span><span class="sxs-lookup"><span data-stu-id="550e2-149">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="550e2-150">Alanın yanındaki oku seçerek **proje dizini** gibi bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="550e2-150">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="550e2-151">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="550e2-151">Choose the **OK** button.</span></span>

   ![Alan değerleri doldurulmuş Dış Araçlar iletişim kutusu.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="550e2-153">Yeni menü öğesi eklenir ve komut istemine Araçlar menüsünden erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="550e2-153">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Visual Studio 'da komut istemi menü öğesi](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="550e2-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="550e2-155">See also</span></span>

- [<span data-ttu-id="550e2-156">.NET Framework Araçları</span><span class="sxs-lookup"><span data-stu-id="550e2-156">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="550e2-157">Dış Araçları Yönetme</span><span class="sxs-lookup"><span data-stu-id="550e2-157">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="550e2-158">Komut satırından Microsoft C++ araç takımını kullanın</span><span class="sxs-lookup"><span data-stu-id="550e2-158">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
