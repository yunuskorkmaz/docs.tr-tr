---
title: Visual Studio için Geliştirici Komut İstemi
ms.date: 08/14/2018
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59af252967a18eca858035fb0a3465d909734ddf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044735"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="c9fde-102">Visual Studio için Geliştirici Komut İstemi</span><span class="sxs-lookup"><span data-stu-id="c9fde-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="c9fde-103">Visual Studio için Geliştirici Komut İstemi, .NET Framework araçları daha kolay kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9fde-103">The Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="c9fde-104">Bu, belirli ortam değişkenlerini otomatik olarak ayarlayan bir komut istemi.</span><span class="sxs-lookup"><span data-stu-id="c9fde-104">It is a command prompt that automatically sets specific environment variables.</span></span>

> [!div class="button"]
> [<span data-ttu-id="c9fde-105">Visual Studio 'Yu indirin</span><span class="sxs-lookup"><span data-stu-id="c9fde-105">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="c9fde-106">Makinenizde komut istemi araması yapın</span><span class="sxs-lookup"><span data-stu-id="c9fde-106">Search for the command prompt on your machine</span></span>

<span data-ttu-id="c9fde-107">Visual Studio sürümüne ve yüklediğiniz ek SDK 'lara bağlı olarak birden çok komut istemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="c9fde-107">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="c9fde-108">Örneğin, Visual Studio'nun 64 bit sürümleri hem 32 bit hem de 64 bit komut istemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9fde-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="c9fde-109">(Çoğu araç için 32-bit ve 64 bit sürümleri aynıdır; ancak, birkaç araç, 32-bit ve 64 bit ortamlara özgü değişiklikler yapar.) Aşağıdaki adımlar çalışmazsa, [makinenizde dosyaları el ile bulmayı](#manually-locate-the-files-on-your-machine) deneyebilir veya [komut satırını Visual Studio 'nun içinden çalıştırabilirsiniz](#run-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="c9fde-109">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [Run the command prompt from inside Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="c9fde-110">Windows 10 ' da</span><span class="sxs-lookup"><span data-stu-id="c9fde-110">In Windows 10</span></span>

1. <span data-ttu-id="c9fde-111">Görev çubuğundaki arama kutusuna, veya `dev` `developer command prompt`gibi aracın adını yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="c9fde-111">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="c9fde-112">Bu, arama örüntüsiyle eşleşen yüklü uygulamaların bir listesini getirir.</span><span class="sxs-lookup"><span data-stu-id="c9fde-112">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="c9fde-113">Farklı bir komut istemi arıyorsanız, gibi farklı bir arama terimi `prompt`girmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-113">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="c9fde-114">**Visual Studio için geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi) seçin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-114">Choose the **Developer Command Prompt for Visual Studio** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="c9fde-115">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="c9fde-115">In Windows 8.1</span></span>

1. <span data-ttu-id="c9fde-116">Klavyede Windows logosu tuşu ![Windows logosu tuşuna basarak Başlangıç ekranına gidin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="c9fde-116">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="c9fde-117">Örneğin, klavyenizde.</span><span class="sxs-lookup"><span data-stu-id="c9fde-117">on your keyboard for example.</span></span>

2. <span data-ttu-id="c9fde-118">**Başlat** ekranında, **CTRL**+tuşuna basarak **uygulamalar** listesini açın ve ardından yazın `V`.</span><span class="sxs-lookup"><span data-stu-id="c9fde-118">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then enter `V`.</span></span> <span data-ttu-id="c9fde-119">Bu, tüm yüklü Visual Studio komut istemlerini içeren bir liste getirir.</span><span class="sxs-lookup"><span data-stu-id="c9fde-119">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="c9fde-120">**Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi) seçin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="c9fde-121">Windows 8 ' de</span><span class="sxs-lookup"><span data-stu-id="c9fde-121">In Windows 8</span></span>

1. <span data-ttu-id="c9fde-122">Klavyede Windows logosu tuşu ![Windows logosu tuşuna basarak Başlangıç ekranına gidin.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="c9fde-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="c9fde-123">Örneğin, klavyenizde.</span><span class="sxs-lookup"><span data-stu-id="c9fde-123">on your keyboard for example.</span></span>

2. <span data-ttu-id="c9fde-124">**Başlat** ekranında klavyede Windows logosu tuşu ![Windows logosu tuşuna basın.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="c9fde-124">On the **Start** screen, press the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="c9fde-125">`+ Z`.</span><span class="sxs-lookup"><span data-stu-id="c9fde-125">`+ Z`.</span></span>

3. <span data-ttu-id="c9fde-126">Ekranın alt kısmındaki **Uygulamalar görünümü** simgesini seçin ve ardından girin `V`.</span><span class="sxs-lookup"><span data-stu-id="c9fde-126">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="c9fde-127">Bu, tüm yüklü Visual Studio komut istemlerini içeren bir liste getirir.</span><span class="sxs-lookup"><span data-stu-id="c9fde-127">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="c9fde-128">**Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi) seçin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-128">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="c9fde-129">Windows 7 ' de</span><span class="sxs-lookup"><span data-stu-id="c9fde-129">In Windows 7</span></span>

1. <span data-ttu-id="c9fde-130">**Başlat**' ı seçin, **tüm programlar**' ı genişletin ve **Microsoft Visual Studio**' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-130">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="c9fde-131">Yüklediğiniz Visual Studio sürümüne bağlı olarak **Visual Studio Araçları**, **Visual Studio komut istemi**veya kullanmak istediğiniz komut istemi ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-131">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="c9fde-132">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümler](https://developer.microsoft.com/windows/downloads/sdk-archive)gibi başka SDK 'lar yüklüyse, ARM, x86 veya x64 mimarileri için ek komut istemleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9fde-132">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="c9fde-133">Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="c9fde-133">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="c9fde-134">Makinenizde dosyaları el ile bulun</span><span class="sxs-lookup"><span data-stu-id="c9fde-134">Manually locate the files on your machine</span></span>

<span data-ttu-id="c9fde-135">Genellikle, yüklediğiniz komut istemlerinin kısayolları, C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017 \ Visual Studio Araçları gibi Visual Studio için **Başlat menüsü** klasörüne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c9fde-135">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="c9fde-136">Ancak, bazı nedenlerle komut istemi araması beklenen sonuçları getirmiyorsa, bu kısayolu makinenizde el ile bulmayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9fde-136">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="c9fde-137">Örneğin, *Vsdevcmd. bat*gibi komut istemi dosyasının adını aramayı deneyin veya C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools gibi Araçlar klasörüne gidin (Visual Studio sürümünüz sürümüne göre yol değişiklikleri) ve yükleme konumu).</span><span class="sxs-lookup"><span data-stu-id="c9fde-137">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="c9fde-138">Komut istemi 'ni Visual Studio 'Nun içinden çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c9fde-138">Run the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="c9fde-139">Daha kolay erişim için Visual Studio Geliştirici Komut İstemi veya başka bir komut istemi, Visual Studio 'daki **Araçlar** menüsüne eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c9fde-139">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="c9fde-140">Aracı kullanılabilir hale getirmek için dış araçlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-140">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="c9fde-141">Adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c9fde-141">Here are the steps:</span></span>

1. <span data-ttu-id="c9fde-142">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="c9fde-142">Open Visual Studio.</span></span>

2. <span data-ttu-id="c9fde-143">**Araçlar** menüsünü ve ardından **dış araçlar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-143">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="c9fde-144">**Dış araçlar** Iletişim kutusunda **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-144">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="c9fde-145">Yeni bir giriş görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c9fde-145">A new entry appears.</span></span>

4. <span data-ttu-id="c9fde-146">Yeni menü öğesi için gibi `Command Prompt`bir başlık girin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-146">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="c9fde-147">**Komut** alanında, başlatmak `%comspec%` istediğiniz dosyayı (veya `C:\Windows\System32\cmd.exe`gibi) belirtin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-147">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="c9fde-148">**Bağımsız değişkenler** alanında, gibi kullanmak `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` istediğiniz belirli komut isteminin nerede bulunacağını belirtin (Bu komut, Visual Studio 2017 Enterprise ile yüklenen Geliştirici komut istemi başlatır).</span><span class="sxs-lookup"><span data-stu-id="c9fde-148">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="c9fde-149">Bu değeri, Visual Studio sürümünüz, sürümünüz ve yükleme konumunuza göre değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-149">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="c9fde-150">**İlk dizin** alanı Için **proje dizini**gibi bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="c9fde-150">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="c9fde-151">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c9fde-151">Choose the **OK** button.</span></span>

   <span data-ttu-id="c9fde-152">Yeni menü öğesi eklenir ve komut istemine **Araçlar** menüsünden erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9fde-152">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

   ![Visual Studio 'da komut istemi menü öğesi](./media/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="c9fde-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9fde-154">See also</span></span>

- [<span data-ttu-id="c9fde-155">Araçlar</span><span class="sxs-lookup"><span data-stu-id="c9fde-155">Tools</span></span>](index.md)
- [<span data-ttu-id="c9fde-156">Dış Araçları Yönetme</span><span class="sxs-lookup"><span data-stu-id="c9fde-156">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
