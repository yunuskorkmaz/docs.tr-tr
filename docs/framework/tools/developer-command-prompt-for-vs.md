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
ms.openlocfilehash: cded8ce271ea0f3d1dbb8fc3d9a072ee4a23d1ee
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149178"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="60bef-102">Visual Studio için geliştirici komut istemi</span><span class="sxs-lookup"><span data-stu-id="60bef-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="60bef-103">Visual Studio için geliştirici komut istemi, .NET Framework araçlarını kolayca kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="60bef-103">The Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="60bef-104">Bu, belirli ortam değişkenlerini otomatik olarak ayarlayan bir komut istemi olur.</span><span class="sxs-lookup"><span data-stu-id="60bef-104">It is a command prompt that automatically sets specific environment variables.</span></span>

> [!div class="button"]
> [<span data-ttu-id="60bef-105">Visual Studio'yu indirin</span><span class="sxs-lookup"><span data-stu-id="60bef-105">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="60bef-106">Komut istemi makinenizde arayın</span><span class="sxs-lookup"><span data-stu-id="60bef-106">Search for the command prompt on your machine</span></span>

<span data-ttu-id="60bef-107">Visual Studio ve ek Sdk'lara yüklediğiniz sürümüne bağlı olarak birden çok komut istemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="60bef-107">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="60bef-108">Örneğin, Visual Studio'nun 64 bit sürümleri hem 32 bit hem de 64 bit komut istemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="60bef-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="60bef-109">(Çoğu araç 32-bit ve 64-bit sürümleri aynıdır; ancak, birkaç araç 32-bit ve 64 bit ortamlara özel değişiklikler.) Aşağıdaki adımlar işe yaramazsa, deneyebileceğiniz [makinenizde dosyaları el ile konumlandırmak](#manually-locate-the-files-on-your-machine) veya [komut isteminden çalıştırın Visual Studio içinde](#run-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="60bef-109">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [Run the command prompt from inside Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="60bef-110">Windows 10</span><span class="sxs-lookup"><span data-stu-id="60bef-110">In Windows 10</span></span>

1. <span data-ttu-id="60bef-111">Görev çubuğundaki arama kutusuna gibi aracının adını yazarak Başlat `dev` veya `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="60bef-111">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="60bef-112">Bu, arama deseniyle eşleşen yüklü uygulamalar listesini getirir.</span><span class="sxs-lookup"><span data-stu-id="60bef-112">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="60bef-113">Gibi farklı bir arama terimi girmek için farklı bir komut istemi arıyorsanız deneyin `prompt`.</span><span class="sxs-lookup"><span data-stu-id="60bef-113">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="60bef-114">Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).</span><span class="sxs-lookup"><span data-stu-id="60bef-114">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="60bef-115">Windows 8.1 içinde</span><span class="sxs-lookup"><span data-stu-id="60bef-115">In Windows 8.1</span></span>

1. <span data-ttu-id="60bef-116">Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.</span><span class="sxs-lookup"><span data-stu-id="60bef-116">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="60bef-117">Üzerinde **Başlat** tuşuna basın, ekran **Ctrl**+**sekmesini** açmak için **uygulamaları** listelemek ve enter `V`.</span><span class="sxs-lookup"><span data-stu-id="60bef-117">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then enter `V`.</span></span> <span data-ttu-id="60bef-118">Bu, tüm yüklü Visual Studio Komut İstemi'ni içeren bir liste getirir.</span><span class="sxs-lookup"><span data-stu-id="60bef-118">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="60bef-119">Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).</span><span class="sxs-lookup"><span data-stu-id="60bef-119">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="60bef-120">Windows 8'de</span><span class="sxs-lookup"><span data-stu-id="60bef-120">In Windows 8</span></span>

1. <span data-ttu-id="60bef-121">Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.</span><span class="sxs-lookup"><span data-stu-id="60bef-121">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="60bef-122">Üzerinde **Başlat** ekranında, Windows logosu tuşuna ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="60bef-122">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="60bef-123">Seçin **uygulamaları görüntüle** ekranın altındaki simgesini ve ardından girin `V`.</span><span class="sxs-lookup"><span data-stu-id="60bef-123">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="60bef-124">Bu, tüm yüklü Visual Studio Komut İstemi'ni içeren bir liste getirir.</span><span class="sxs-lookup"><span data-stu-id="60bef-124">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="60bef-125">Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).</span><span class="sxs-lookup"><span data-stu-id="60bef-125">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="60bef-126">Windows 7 '</span><span class="sxs-lookup"><span data-stu-id="60bef-126">In Windows 7</span></span>

1. <span data-ttu-id="60bef-127">Seçin **Başlat**, genişletme **tüm programlar**ve ardından **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="60bef-127">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="60bef-128">Yüklemiş Visual Studio sürümüne bağlı olarak, seçin **Visual Studio Araçları**, **Visual Studio komut istemi**, veya kullanmak istediğiniz komut istemi.</span><span class="sxs-lookup"><span data-stu-id="60bef-128">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="60bef-129">Diğer SDK'lar gibi varsa [Windows 10 SDK'sı](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümleri](https://developer.microsoft.com/windows/downloads/sdk-archive), ek komut istemleri için ARM, x 86 veya x64 mimariler görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60bef-129">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="60bef-130">Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="60bef-130">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="60bef-131">Makinenizde dosyaları el ile bulun</span><span class="sxs-lookup"><span data-stu-id="60bef-131">Manually locate the files on your machine</span></span>

<span data-ttu-id="60bef-132">Genellikle, yüklediğiniz komut istemlerine kısayolları yerleştirilir **Başlat menüsü** C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Araçları gibi Visual Studio için klasör.</span><span class="sxs-lookup"><span data-stu-id="60bef-132">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="60bef-133">Ancak bazı nedenlerden dolayı için komut istemi arama beklenen sonuçları getirmek değil, kısayol makinenizde el ile bulmak deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60bef-133">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="60bef-134">Komut istemi dosyasının adı için gibi aramayı deneyin *VsDevCmd.bat*, veya C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (yolu değişiklikleri Görselinizi göre gibi Araçlar klasörüne gidin Studio sürümü, sürümü ve yükleme konumu).</span><span class="sxs-lookup"><span data-stu-id="60bef-134">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="60bef-135">Komut İstemi'nden çalıştırmak Visual Studio içinde</span><span class="sxs-lookup"><span data-stu-id="60bef-135">Run the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="60bef-136">Daha kolay erişim için Visual Studio Geliştirici komut istemi veya herhangi başka bir komut istemi, ekleyebilirsiniz **Araçları** Visual Studio'daki menü.</span><span class="sxs-lookup"><span data-stu-id="60bef-136">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="60bef-137">Aracı kullanabilmek için dış araçları listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="60bef-137">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="60bef-138">Adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="60bef-138">Here are the steps:</span></span>

1. <span data-ttu-id="60bef-139">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="60bef-139">Open Visual Studio.</span></span>

2. <span data-ttu-id="60bef-140">Seçin **Araçları** menüsünü seçip **dış Araçları**.</span><span class="sxs-lookup"><span data-stu-id="60bef-140">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="60bef-141">Üzerinde **dış Araçlar** iletişim kutusunda **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="60bef-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="60bef-142">Yeni bir giriş belirir.</span><span class="sxs-lookup"><span data-stu-id="60bef-142">A new entry appears.</span></span>

4. <span data-ttu-id="60bef-143">Girin bir **başlık** gibi yeni menü öğesi için `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="60bef-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="60bef-144">İçinde **komut** alanında, istediğiniz gibi başlatmak için dosyayı belirtin `%comspec%` veya `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="60bef-144">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="60bef-145">İçinde **bağımsız değişkenleri** alanında, kullanmak istediğiniz gibi belirli komut istemini nerede bulacağını belirtin `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (Bu komut, Visual Studio 2017 Enterprise ile yüklü Geliştirici komut istemi başlatılır).</span><span class="sxs-lookup"><span data-stu-id="60bef-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="60bef-146">Visual Studio sürümü, sürümü ve yükleme konumuna göre bu değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="60bef-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="60bef-147">İçin bir değer seçin **başlangıç dizini** gibi alan **proje dizini**.</span><span class="sxs-lookup"><span data-stu-id="60bef-147">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="60bef-148">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="60bef-148">Choose the **OK** button.</span></span>

   <span data-ttu-id="60bef-149">Yeni menü öğesi eklendi ve Komut İstemi'nden erişebilir **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="60bef-149">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

   ![Visual Studio komut istemi menü öğesi](media/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="60bef-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60bef-151">See also</span></span>

- [<span data-ttu-id="60bef-152">Araçlar</span><span class="sxs-lookup"><span data-stu-id="60bef-152">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="60bef-153">Dış Araçları Yönetme</span><span class="sxs-lookup"><span data-stu-id="60bef-153">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
