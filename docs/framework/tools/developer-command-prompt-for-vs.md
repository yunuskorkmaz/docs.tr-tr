---
title: Visual Studio için geliştirici komut istemi
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
ms.openlocfilehash: 4c95074190419dd3e984c7659ede917b83b97f08
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752327"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="44809-102">Visual Studio için geliştirici komut istemi</span><span class="sxs-lookup"><span data-stu-id="44809-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="44809-103">Visual Studio için geliştirici komut istemi, .NET Framework araçlarını kolayca kullanmanıza olanak tanıyan ortam değişkenlerini otomatik olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="44809-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span>

> [!div class="button"]
[<span data-ttu-id="44809-104">Visual Studio'yu indirin</span><span class="sxs-lookup"><span data-stu-id="44809-104">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="44809-105">Komut istemi makinenizde arama</span><span class="sxs-lookup"><span data-stu-id="44809-105">Searching for the command prompt on your machine</span></span>

<span data-ttu-id="44809-106">Visual Studio ve ek Sdk'lara yüklediğiniz sürümüne bağlı olarak birden çok komut istemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="44809-106">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="44809-107">Örneğin, Visual Studio'nun 64 bit sürümleri hem 32 bit hem de 64 bit komut istemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44809-107">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="44809-108">(Çoğu araç 32-bit ve 64-bit sürümleri aynıdır; ancak, birkaç araç 32-bit ve 64 bit ortamlara özel değişiklikler.) Aşağıdaki adımlar işe yaramazsa, deneyebileceğiniz [makinenizde dosyaları el ile bulma](#manually-locating-the-files-on-your-machine) veya [komut isteminden çalıştırma Visual Studio içinde](#running-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="44809-108">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locating the files on your machine](#manually-locating-the-files-on-your-machine) or [Running the command prompt from inside Visual Studio](#running-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="44809-109">Windows 10</span><span class="sxs-lookup"><span data-stu-id="44809-109">In Windows 10</span></span>

1. <span data-ttu-id="44809-110">Görev çubuğundaki arama kutusuna gibi aracının adını yazarak Başlat `dev` veya `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="44809-110">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="44809-111">Bu, arama deseniyle eşleşen yüklü uygulamalar listesini getirir.</span><span class="sxs-lookup"><span data-stu-id="44809-111">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="44809-112">Gibi farklı bir arama terimi girmek için farklı bir komut istemi arıyorsanız deneyin `prompt`.</span><span class="sxs-lookup"><span data-stu-id="44809-112">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="44809-113">Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).</span><span class="sxs-lookup"><span data-stu-id="44809-113">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="44809-114">Windows 8.1 içinde</span><span class="sxs-lookup"><span data-stu-id="44809-114">In Windows 8.1</span></span>

1. <span data-ttu-id="44809-115">Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.</span><span class="sxs-lookup"><span data-stu-id="44809-115">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="44809-116">Üzerinde **Başlat** tuşuna basın, ekran `CTRL + TAB` açmak için **uygulamaları** listelemek ve enter `V`.</span><span class="sxs-lookup"><span data-stu-id="44809-116">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="44809-117">Bu, tüm yüklü Visual Studio Komut İstemi'ni içeren bir liste getirir.</span><span class="sxs-lookup"><span data-stu-id="44809-117">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="44809-118">Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).</span><span class="sxs-lookup"><span data-stu-id="44809-118">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="44809-119">Windows 8'de</span><span class="sxs-lookup"><span data-stu-id="44809-119">In Windows 8</span></span>

1. <span data-ttu-id="44809-120">Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.</span><span class="sxs-lookup"><span data-stu-id="44809-120">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="44809-121">Üzerinde **Başlat** ekranında, Windows logosu tuşuna ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="44809-121">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="44809-122">Seçin **uygulamaları görüntüle** ekranın altındaki simgesini ve ardından girin `V`.</span><span class="sxs-lookup"><span data-stu-id="44809-122">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="44809-123">Bu, tüm yüklü Visual Studio Komut İstemi'ni içeren bir liste getirir.</span><span class="sxs-lookup"><span data-stu-id="44809-123">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="44809-124">Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).</span><span class="sxs-lookup"><span data-stu-id="44809-124">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="44809-125">Windows 7 '</span><span class="sxs-lookup"><span data-stu-id="44809-125">In Windows 7</span></span>

1. <span data-ttu-id="44809-126">Seçin **Başlat**, genişletme **tüm programlar**ve ardından **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="44809-126">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="44809-127">Yüklemiş Visual Studio sürümüne bağlı olarak, seçin **Visual Studio Araçları**, **Visual Studio komut istemi**, veya kullanmak istediğiniz komut istemi.</span><span class="sxs-lookup"><span data-stu-id="44809-127">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="44809-128">Diğer SDK'lar gibi varsa [Windows 10 SDK'sı](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümleri](https://developer.microsoft.com/windows/downloads/sdk-archive), ek komut istemleri için ARM, x 86 veya x64 mimariler görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44809-128">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="44809-129">Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="44809-129">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="44809-130">Makinenizde dosyaları el ile bulun</span><span class="sxs-lookup"><span data-stu-id="44809-130">Manually locate the files on your machine</span></span>

<span data-ttu-id="44809-131">Genellikle, yüklediğiniz komut istemlerine kısayolları yerleştirilir **Başlat menüsü** C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Araçları gibi Visual Studio için klasör.</span><span class="sxs-lookup"><span data-stu-id="44809-131">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="44809-132">Ancak bazı nedenlerden dolayı için komut istemi arama beklenen sonuçları getirmek değil, kısayol makinenizde el ile bulmak deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44809-132">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="44809-133">Komut istemi dosyasının adı için gibi aramayı deneyin *VsDevCmd.bat*, veya C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (yolu değişiklikleri Görselinizi göre gibi Araçlar klasörüne gidin Studio sürümü, sürümü ve yükleme konumu).</span><span class="sxs-lookup"><span data-stu-id="44809-133">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="44809-134">Komutunu çalıştırırsanız Visual Studio içinde sor</span><span class="sxs-lookup"><span data-stu-id="44809-134">Run command prompt from inside Visual Studio</span></span>

<span data-ttu-id="44809-135">Daha kolay erişim için Visual Studio Geliştirici komut istemi veya herhangi başka bir komut istemi, ekleyebilirsiniz **Araçları** Visual Studio'daki menü.</span><span class="sxs-lookup"><span data-stu-id="44809-135">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="44809-136">Aracı kullanabilmek için dış araçları listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="44809-136">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="44809-137">Adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="44809-137">Here are the steps:</span></span>

1. <span data-ttu-id="44809-138">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="44809-138">Open Visual Studio.</span></span>

2. <span data-ttu-id="44809-139">Seçin **Araçları** menüsünü seçip **dış Araçları**.</span><span class="sxs-lookup"><span data-stu-id="44809-139">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="44809-140">Üzerinde **dış Araçlar** iletişim kutusunda **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="44809-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="44809-141">Yeni bir giriş belirir.</span><span class="sxs-lookup"><span data-stu-id="44809-141">A new entry appears.</span></span>

4. <span data-ttu-id="44809-142">Girin bir **başlık** gibi yeni menü öğesi için `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="44809-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="44809-143">İçinde **komut** alanında, istediğiniz gibi başlatmak için dosyayı belirtin `%comspec%` veya `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="44809-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="44809-144">İçinde **bağımsız değişkenleri** alanında, kullanmak istediğiniz gibi belirli komut istemini nerede bulacağını belirtin `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (Bu komut, Visual Studio 2017 Enterprise ile yüklü Geliştirici komut istemi başlatılır).</span><span class="sxs-lookup"><span data-stu-id="44809-144">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="44809-145">Visual Studio sürümü, sürümü ve yükleme konumuna göre bu değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="44809-145">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="44809-146">İçin bir değer seçin **başlangıç dizini** gibi alan **proje dizini**.</span><span class="sxs-lookup"><span data-stu-id="44809-146">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="44809-147">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="44809-147">Choose the **OK** button.</span></span>

   <span data-ttu-id="44809-148">Yeni menü öğesi eklendi ve Komut İstemi'nden erişebilir **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="44809-148">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="44809-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44809-149">See also</span></span>

- [<span data-ttu-id="44809-150">Araçlar</span><span class="sxs-lookup"><span data-stu-id="44809-150">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="44809-151">Dış Araçları Yönetme</span><span class="sxs-lookup"><span data-stu-id="44809-151">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
