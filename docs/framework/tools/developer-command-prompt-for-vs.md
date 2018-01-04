---
title: "Visual Studio için geliştirici komut istemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8bd7baec77e6e776f93a2a13156d66c1199f918
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="68a45-102">Visual Studio için geliştirici komut istemi</span><span class="sxs-lookup"><span data-stu-id="68a45-102">Developer Command Prompt for Visual Studio</span></span>
<span data-ttu-id="68a45-103">Visual Studio için geliştirici komut istemi, .NET Framework araçları kolayca kullanmanıza olanak ortam değişkenlerini otomatik olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="68a45-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span> <span data-ttu-id="68a45-104">Geliştirici komut istemi tam veya topluluk Visual Studio sürümleriyle yüklenir.</span><span class="sxs-lookup"><span data-stu-id="68a45-104">The Developer Command Prompt is installed with full or community editions of Visual Studio.</span></span> <span data-ttu-id="68a45-105">Visual Studio Express sürümleri ile yüklenmedi.</span><span class="sxs-lookup"><span data-stu-id="68a45-105">It is not installed with the Express versions of Visual Studio.</span></span>  
  
<a name="find"></a>   
## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="68a45-106">Komut istemi makinenizde arama</span><span class="sxs-lookup"><span data-stu-id="68a45-106">Searching for the Command Prompt on your machine</span></span>  
 <span data-ttu-id="68a45-107">Visual Studio ve yüklemiş olduğunuz herhangi bir ek SDK sürümüne bağlı olarak birden çok komut istemlerini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a45-107">You may see multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="68a45-108">Örneğin, Visual Studio'nun 64 bit sürümleri hem 32 bit hem de 64 bit komut istemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="68a45-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="68a45-109">(Çoğu aracın 32 bit ve 64 bit sürümleri aynıdır; ancak, birkaç araç, 32 bit ve 64 bit ortamlara özel değişiklikler yapar.) Aşağıdaki adımlar işe yaramazsa, deneyebilirsiniz [el ile makinenizde dosyaları bulma](#alternative) veya [komutunu çalıştırarak Visual Studio içinde sor](#visualstudio).</span><span class="sxs-lookup"><span data-stu-id="68a45-109">(The 32-bit and 64-bit versions of most tools are identical; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the steps below don't work, you can try [Manually locating the files on your machine](#alternative) or [Running command prompt from inside Visual Studio](#visualstudio).</span></span>  
  
 <span data-ttu-id="68a45-110">**Windows 10**</span><span class="sxs-lookup"><span data-stu-id="68a45-110">**In Windows 10**</span></span>  
  
1.  <span data-ttu-id="68a45-111">Açık **Başlat** Windows logosu tuşuna basarak menüsünde ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.</span><span class="sxs-lookup"><span data-stu-id="68a45-111">Open the **Start** menu, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="68a45-112">Üzerinde **Başlat** menüsünde girin `dev`.</span><span class="sxs-lookup"><span data-stu-id="68a45-112">On the **Start** menu, enter `dev`.</span></span> <span data-ttu-id="68a45-113">Bu, arama deseniyle eşleşen yüklü uygulamaların bir listesini getirir.</span><span class="sxs-lookup"><span data-stu-id="68a45-113">This will bring a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="68a45-114">Farklı bir komut isteminde arıyorsanız, farklı bir arama terimi gibi girmeyi deneyin `prompt`.</span><span class="sxs-lookup"><span data-stu-id="68a45-114">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>  
  
3.  <span data-ttu-id="68a45-115">Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).</span><span class="sxs-lookup"><span data-stu-id="68a45-115">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="68a45-116">**Windows 8.1**</span><span class="sxs-lookup"><span data-stu-id="68a45-116">**In Windows 8.1**</span></span>  
  
1.  <span data-ttu-id="68a45-117">Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.</span><span class="sxs-lookup"><span data-stu-id="68a45-117">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="68a45-118">Üzerinde **Başlat** ekranında, basın `CTRL + TAB` açmak için **uygulamaları** listelemek ve enter `V`.</span><span class="sxs-lookup"><span data-stu-id="68a45-118">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="68a45-119">Bu, tüm yüklü Visual Studio komut istemleri içeren bir liste getirir.</span><span class="sxs-lookup"><span data-stu-id="68a45-119">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
3.  <span data-ttu-id="68a45-120">Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).</span><span class="sxs-lookup"><span data-stu-id="68a45-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="68a45-121">**Windows 8**</span><span class="sxs-lookup"><span data-stu-id="68a45-121">**In Windows 8**</span></span>  
  
1.  <span data-ttu-id="68a45-122">Git **Başlat** ekranında Windows logosu tuşuna basarak ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") klavyenizde örneğin.</span><span class="sxs-lookup"><span data-stu-id="68a45-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="68a45-123">Üzerinde **Başlat** ekranında, Windows logosu tuşuna ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="68a45-123">On the **Start** screen, press the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>  
  
3.  <span data-ttu-id="68a45-124">Seçin **uygulamaları görüntülemek** ekranın alt kısmındaki simgesine tıklayın ve ardından girin `V`.</span><span class="sxs-lookup"><span data-stu-id="68a45-124">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="68a45-125">Bu, tüm yüklü Visual Studio komut istemleri içeren bir liste getirir.</span><span class="sxs-lookup"><span data-stu-id="68a45-125">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
4.  <span data-ttu-id="68a45-126">Seçin **Geliştirici komut istemi** (veya kullanmak istediğiniz komut istemi).</span><span class="sxs-lookup"><span data-stu-id="68a45-126">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="68a45-127">**Windows 7**</span><span class="sxs-lookup"><span data-stu-id="68a45-127">**In Windows 7**</span></span>  
  
1.  <span data-ttu-id="68a45-128">Seçin **Başlat**, genişletin **tüm programlar**, genişletin ve ardından **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="68a45-128">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="68a45-129">Yüklü olan Visual Studio sürümüne bağlı olarak seçin **Visual Studio Araçları**, **Visual Studio komut istemi**, veya kullanmak istediğiniz komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="68a45-129">Depending on the version of Visual Studio you have installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>  
  
 <span data-ttu-id="68a45-130">Varsa [Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) veya [Windows Phone SDK'sı](https://dev.windowsphone.com/downloadsdk) yüklüyse, ek komutu ister ARM için x 86 veya x64 mimarileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a45-130">If you have the [Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) or [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk) installed, you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="68a45-131">Hangi komut istemi sürümünü kullanmanız gerektiğini belirlemek için, tek tek araçlara ilişkin belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="68a45-131">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>  
  
<a name="alternative"></a>   
## <a name="manually-locating-the-files-on-your-machine"></a><span data-ttu-id="68a45-132">El ile makinenizde dosyaları bulma</span><span class="sxs-lookup"><span data-stu-id="68a45-132">Manually locating the files on your machine</span></span>  
  <span data-ttu-id="68a45-133">Genellikle, yüklü olan komut istemleri kısayolları adresindeki yerleştirilecek **Başlat menüsü** C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio olduğu gibi Visual Studio için klasör Araçları.</span><span class="sxs-lookup"><span data-stu-id="68a45-133">Usually, the shortcuts for the command prompts you have installed will be placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Tools.</span></span>    <span data-ttu-id="68a45-134">Ancak herhangi bir nedenle komut satırından arama beklenen sonuçları elde etmek değil, el ile kullanmak için makinenizde kısayol bulun deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a45-134">But if for some reason, searching for the command prompt doesn't yield the expected results, you can try to manually locate the shortcut on your machine in order to use it.</span></span>   <span data-ttu-id="68a45-135">VsDevCmd.bat gibi bir komut istemi dosyasının adı için arama yapmayı deneyin veya C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\Tools gibi Araçlar klasörüne gidin (Visual Studio sürümü ve yükleme konumuna göre yolu değiştirir).</span><span class="sxs-lookup"><span data-stu-id="68a45-135">Try searching for the name of the command prompt file such as VsDevCmd.bat or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools (path will change according to your Visual Studio version and installation location).</span></span>  
  
<a name="visualstudio"></a>   
## <a name="running-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="68a45-136">Komutunu çalıştırarak Visual Studio içinde sor</span><span class="sxs-lookup"><span data-stu-id="68a45-136">Running command prompt from inside Visual Studio</span></span>  
 <span data-ttu-id="68a45-137">Daha kolay erişim için Visual Studio Geliştirici komut istemi veya herhangi bir komut istemi Visual Studio, Araçlar menüsünden harici araçlar listesine ekleyerek ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a45-137">For easier access, you can add the Visual Studio Developer Command Prompt  or any other command prompt to the Tools menu on Visual Studio, by adding it to the external tools list.</span></span> <span data-ttu-id="68a45-138">Bu, nasıl gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a45-138">This is how you can accomplish that:</span></span>  
  
1.  <span data-ttu-id="68a45-139">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="68a45-139">Open Visual Studio.</span></span>  
  
2.  <span data-ttu-id="68a45-140">Seçin **Araçları** menü ve **harici araçlar...** .</span><span class="sxs-lookup"><span data-stu-id="68a45-140">Select the **Tools** menu and choose **External Tools...**.</span></span>  
  
3.  <span data-ttu-id="68a45-141">Üzerinde **Harici Araçlar** iletişim kutusunda, seçin **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="68a45-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="68a45-142">Yeni bir giriş belirir</span><span class="sxs-lookup"><span data-stu-id="68a45-142">A new entry appears</span></span>  
  
4.  <span data-ttu-id="68a45-143">Girin bir **başlık** gibi yeni menü öğesi için `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="68a45-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>  
  
5.  <span data-ttu-id="68a45-144">İçinde **komutu** alanında, istediğiniz gibi başlatmak için dosyayı belirtin `%comspec%` veya `C:\Windows\System32\cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="68a45-144">In the **Command** field, specify the file you want to launch such as `%comspec%` or `C:\Windows\System32\cmd.exe` .</span></span>  
  
6.  <span data-ttu-id="68a45-145">İçinde **bağımsız değişkenleri** alanında, kullanmak istediğiniz gibi belirli komut istemi nerede bulacağını belirtin `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (Bu yüklenmiş Geliştirici komut istemi başlatacak [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="68a45-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (this will launch the Developer Command Prompt installed with [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]).</span></span> <span data-ttu-id="68a45-146">Bu değer, Visual Studio sürümü ve yükleme konumuna göre değiştirilmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="68a45-146">This value needs to be changed according to your Visual Studio version and installation location.</span></span>  
  
7.  <span data-ttu-id="68a45-147">İçin bir değer seçin **başlangıç dizini** gibi alan **proje dizinine** .</span><span class="sxs-lookup"><span data-stu-id="68a45-147">Choose a value for the **Initial directory** field such as **Project Directory** .</span></span>  
  
8.  <span data-ttu-id="68a45-148">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="68a45-148">Choose the **OK** button.</span></span>  
  
 <span data-ttu-id="68a45-149">Bundan sonra yeni menü öğesi eklendi ve komut isteminden erişebilirsiniz **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="68a45-149">After that, the new menu item is added and you can access the command prompt from the **Tools** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68a45-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68a45-150">See Also</span></span>  
 [<span data-ttu-id="68a45-151">Araçlar</span><span class="sxs-lookup"><span data-stu-id="68a45-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="68a45-152">Dış Araçları Yönetme</span><span class="sxs-lookup"><span data-stu-id="68a45-152">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
