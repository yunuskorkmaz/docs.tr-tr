---
title: Visual Studio için geliştirici komut istemi
ms.date: 06/18/2018
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
ms.openlocfilehash: 7e91822f172de8700b04847541c4b80010a22b53
ms.sourcegitcommit: 3d42e1d73e21c35c540dd4adbea23efcbe1b8b0a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270493"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="5356d-102">Visual Studio için geliştirici komut istemi</span><span class="sxs-lookup"><span data-stu-id="5356d-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="5356d-103">Visual Studio için geliştirici komut istemi, .NET Framework araçları kolayca kullanmanıza olanak ortam değişkenlerini otomatik olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5356d-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span> <span data-ttu-id="5356d-104">Geliştirici komut istemi tam veya topluluk Visual Studio sürümleriyle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5356d-104">The Developer Command Prompt is installed with full or community editions of Visual Studio.</span></span> <span data-ttu-id="5356d-105">Visual Studio Express sürümleri ile yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="5356d-105">It isn't installed with the Express versions of Visual Studio.</span></span>

> [!div class="button"]
[<span data-ttu-id="5356d-106">Visual Studio indirme</span><span class="sxs-lookup"><span data-stu-id="5356d-106">Download Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="5356d-107">Komut istemi makinenizde arama</span><span class="sxs-lookup"><span data-stu-id="5356d-107">Searching for the Command Prompt on your machine</span></span>

<span data-ttu-id="5356d-108">Visual Studio ve yüklemiş olduğunuz herhangi bir ek SDK sürümüne bağlı olarak birçok komut istemlerini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5356d-108">You may see many command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="5356d-109">Örneğin, Visual Studio'nun 64 bit sürümleri hem 32 bit hem de 64 bit komut istemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5356d-109">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="5356d-110">(Çoğu araçlarının 32-bit ve 64 bit sürümleri aynıdır; ancak, bazı araçları 32-bit ve 64-bit ortamlar için belirli değişiklik.) Aşağıdaki adımlar işe yaramazsa, deneyebilirsiniz [el ile makinenizde dosyaları bulma](#manually-locating-the-files-on-your-machine) veya [komutunu çalıştırarak Visual Studio içinde sor](#running-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="5356d-110">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locating the files on your machine](#manually-locating-the-files-on-your-machine) or [Running command prompt from inside Visual Studio](#running-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="5356d-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="5356d-111">In Windows 10</span></span>

1. <span data-ttu-id="5356d-112">Görev çubuğunda arama kutusuna, aracı adı gibi yazmaya başlayın `dev` veya `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="5356d-112">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="5356d-113">Bu, arama deseniyle eşleşen yüklü uygulamaların bir listesini getirir.</span><span class="sxs-lookup"><span data-stu-id="5356d-113">This brings a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="5356d-114">Farklı bir komut isteminde arıyorsanız, farklı bir arama terimi gibi girmeyi deneyin `prompt`.</span><span class="sxs-lookup"><span data-stu-id="5356d-114">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="5356d-115">Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).</span><span class="sxs-lookup"><span data-stu-id="5356d-115">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="5356d-116">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="5356d-116">In Windows 8.1</span></span>

1. <span data-ttu-id="5356d-117">Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.</span><span class="sxs-lookup"><span data-stu-id="5356d-117">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="5356d-118">Üzerinde **Başlat** ekranında, basın `CTRL + TAB` açmak için **uygulamaları** listelemek ve enter `V`.</span><span class="sxs-lookup"><span data-stu-id="5356d-118">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="5356d-119">Bu, tüm yüklü Visual Studio komut istemleri içeren bir liste getirir.</span><span class="sxs-lookup"><span data-stu-id="5356d-119">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="5356d-120">Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).</span><span class="sxs-lookup"><span data-stu-id="5356d-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="5356d-121">Windows 8</span><span class="sxs-lookup"><span data-stu-id="5356d-121">In Windows 8</span></span>

1. <span data-ttu-id="5356d-122">Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.</span><span class="sxs-lookup"><span data-stu-id="5356d-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="5356d-123">Üzerinde **Başlat** ekranında, Windows logosu tuşuna ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="5356d-123">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="5356d-124">Seçin **uygulamaları görüntülemek** ekranın alt kısmındaki simgesine tıklayın ve ardından girin `V`.</span><span class="sxs-lookup"><span data-stu-id="5356d-124">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="5356d-125">Bu, tüm yüklü Visual Studio komut istemleri içeren bir liste getirir.</span><span class="sxs-lookup"><span data-stu-id="5356d-125">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="5356d-126">Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).</span><span class="sxs-lookup"><span data-stu-id="5356d-126">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="5356d-127">Windows 7</span><span class="sxs-lookup"><span data-stu-id="5356d-127">In Windows 7</span></span>

1. <span data-ttu-id="5356d-128">Seçin **Başlat**, genişletin **tüm programlar**, genişletin ve ardından **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="5356d-128">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="5356d-129">Visual Studio, yükledim sürümüne bağlı olarak seçin **Visual Studio Araçları**, **Visual Studio komut istemi**, veya kullanmak istediğiniz komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="5356d-129">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="5356d-130">Yüklü aşağıdaki gibi diğer SDK varsa [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) veya [önceki sürümler](https://developer.microsoft.com/windows/downloads/sdk-archive) yüklüyse, ek komutu ister ARM için x 86 veya x64 mimarileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5356d-130">If you have other SDKs installed such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive) installed, you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="5356d-131">Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="5356d-131">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locating-the-files-on-your-machine"></a><span data-ttu-id="5356d-132">El ile makinenizde dosyaları bulma</span><span class="sxs-lookup"><span data-stu-id="5356d-132">Manually locating the files on your machine</span></span>

<span data-ttu-id="5356d-133">Genellikle, yüklü olan komut istemleri kısayolları yerleştirilmiş **Başlat menüsü** C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Araçları gibi Visual Studio için klasör.</span><span class="sxs-lookup"><span data-stu-id="5356d-133">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="5356d-134">Ancak herhangi bir nedenle komut satırından arama beklenen sonuçları değil getirirseniz, el ile kısayol makinenizde bulun deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5356d-134">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="5356d-135">Komut istemi dosya adını gibi arama yapmayı deneyin *VsDevCmd.bat*, veya C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (yolu göre değişiklikler, Visual gibi Araçlar klasörüne gidin Studio sürümü, sürümü ve yükleme konumu).</span><span class="sxs-lookup"><span data-stu-id="5356d-135">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="running-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="5356d-136">Komutunu çalıştırarak Visual Studio içinde sor</span><span class="sxs-lookup"><span data-stu-id="5356d-136">Running command prompt from inside Visual Studio</span></span>

<span data-ttu-id="5356d-137">Daha kolay erişim için Visual Studio Geliştirici komut istemi veya herhangi bir komut istemi Visual Studio, Araçlar menüsünden harici araçlar listesine ekleyerek ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5356d-137">For easier access, you can add the Visual Studio Developer Command Prompt  or any other command prompt to the Tools menu on Visual Studio, by adding it to the external tools list.</span></span> <span data-ttu-id="5356d-138">Bu, nasıl gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5356d-138">This is how you can accomplish that:</span></span>

1. <span data-ttu-id="5356d-139">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="5356d-139">Open Visual Studio.</span></span>

2. <span data-ttu-id="5356d-140">Seçin **Araçları** menü ve **Harici Araçlar**.</span><span class="sxs-lookup"><span data-stu-id="5356d-140">Select the **Tools** menu and choose **External Tools**.</span></span>

3. <span data-ttu-id="5356d-141">Üzerinde **Harici Araçlar** iletişim kutusunda, seçin **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5356d-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="5356d-142">Yeni bir giriş belirir.</span><span class="sxs-lookup"><span data-stu-id="5356d-142">A new entry appears.</span></span>

4. <span data-ttu-id="5356d-143">Girin bir **başlık** gibi yeni menü öğesi için `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="5356d-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="5356d-144">İçinde **komutu** alanında, istediğiniz gibi başlatmak için dosyayı belirtin `%comspec%` veya `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="5356d-144">In the **Command** field, specify the file you want to launch such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="5356d-145">İçinde **bağımsız değişkenleri** alanında, kullanmak istediğiniz gibi belirli komut istemi nerede bulacağını belirtin `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (Bu komutu ile Visual Studio 2017 Enterprise yüklü Geliştirici komut istemi başlatır).</span><span class="sxs-lookup"><span data-stu-id="5356d-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="5356d-146">Visual Studio sürümü, sürümü ve yükleme konumuna göre bu değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5356d-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="5356d-147">İçin bir değer seçin **başlangıç dizini** gibi alan **proje dizinine**.</span><span class="sxs-lookup"><span data-stu-id="5356d-147">Choose a value for the **Initial directory** field such as **Project Directory**.</span></span>

8. <span data-ttu-id="5356d-148">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5356d-148">Choose the **OK** button.</span></span>

<span data-ttu-id="5356d-149">Bundan sonra yeni menü öğesi eklendi ve komut isteminden erişebilirsiniz **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="5356d-149">After that, the new menu item is added and you can access the command prompt from the **Tools** menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="5356d-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5356d-150">See also</span></span>

 [<span data-ttu-id="5356d-151">Araçlar</span><span class="sxs-lookup"><span data-stu-id="5356d-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="5356d-152">Dış Araçları Yönetme</span><span class="sxs-lookup"><span data-stu-id="5356d-152">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)  
