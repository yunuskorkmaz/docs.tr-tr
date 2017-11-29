---
title: "Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğine Yükleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 23a1d8c638b198c31d7c83aaf3f216b465f01453
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="e8ef3-102">Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğine Yükleme</span><span class="sxs-lookup"><span data-stu-id="e8ef3-102">How to: Install an Assembly into the Global Assembly Cache</span></span>
<span data-ttu-id="e8ef3-103">Bir katı adlı derlemeyi genel derleme önbelleğine (GAC) yüklemenin iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="e8ef3-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC):</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e8ef3-104">Yalnızca katı adlı derlemeler GAC içine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="e8ef3-105">Tanımlayıcı adlı bir derleme oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi tanımlayıcı adla oturum](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="e8ef3-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
-   <span data-ttu-id="e8ef3-106">Kullanarak [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span><span class="sxs-lookup"><span data-stu-id="e8ef3-106">Using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span>  
  
     <span data-ttu-id="e8ef3-107">Bunu, Visual Studio 2012 ve Visual Studio 2013'te bir InstallShield Limited Edition Projesi oluşturarak yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-107">You do this in Visual Studio 2012 and Visual Studio 2013 by creating an InstallShield Limited Edition Project.</span></span>  
  
     <span data-ttu-id="e8ef3-108">Bu, genel derleme önbelleğine derlemeler eklemenin önerilen ve en yaygın yoludur.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-108">This is the recommended and most common way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="e8ef3-109">Yükleyici, genel derleme önbelleğindeki derlemelerin referans amaçlı sayımını ve başka yararları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-109">The installer provides reference counting of assemblies in the global assembly cache, plus other benefits.</span></span>  
  
-   <span data-ttu-id="e8ef3-110">Kullanarak [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e8ef3-110">Using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
     <span data-ttu-id="e8ef3-111">Genel derleme önbelleğine katı adlı derlemeler eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için Gacutil.exe'yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-111">You can use Gacutil.exe to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e8ef3-112">Gacutil.exe yalnızca geliştirme amaçlıdır ve genel bütünleştirilmiş kod önbelleğine üretim derlemeleri yüklemek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8ef3-113">.NET Framework önceki sürümlerde Shfusion.dll Windows kabuk uzantısı, dosya Gezgini'nde sürükleyerek derlemelerini yüklemek etkin.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-113">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in File Explorer.</span></span> <span data-ttu-id="e8ef3-114">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-114">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a><span data-ttu-id="e8ef3-115">Genel Derleme Önbelleği aracını (Gacutil.exe) kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-115">To use the Global Assembly Cache tool (Gacutil.exe)</span></span>  
  
1.  <span data-ttu-id="e8ef3-116">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="e8ef3-116">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="e8ef3-117">**Gacutil -i** \< *derleme adı*></span><span class="sxs-lookup"><span data-stu-id="e8ef3-117">**gacutil -i** \<*assembly name*></span></span>  
  
     <span data-ttu-id="e8ef3-118">Bu komutta *derleme adı* genel derleme önbelleğinde yüklenecek derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-118">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>  
  
 <span data-ttu-id="e8ef3-119">Aşağıdaki örnek, bir dosya adı ile bir derlemeyi yükler `hello.dll` genel derleme önbelleğine.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-119">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>  
  
```  
gacutil -i hello.dll  
```  
  
 <span data-ttu-id="e8ef3-120">Daha fazla bilgi için bkz: [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e8ef3-120">For more information, see [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
### <a name="to-use-an-installshield-limited-edition-project"></a><span data-ttu-id="e8ef3-121">Bir InstallShield Limited Edition Projesi'ni kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e8ef3-121">To use an InstallShield Limited Edition Project</span></span>  
  
1.  <span data-ttu-id="e8ef3-122">Kurulum ve dağıtım paketi, çözümünüz için kısayol menüsünü açarak ve ardından seçme çözümünüze ekleyin **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-122">Add a setup and deployment package to your solution by opening the shortcut menu for your solution, and then choosing **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="e8ef3-123">İçinde **Yeni Proje Ekle** iletişim kutusunda **yüklü** klasörünü seçin **diğer proje türleri**, **Kurulum ve dağıtım**, **InstallShield Limited Edition**ve projenizin bir ad verin.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-123">In the **Add New Project** dialog box, in the **Installed** folder, choose **Other Project Types**,  **Setup and Deployment**, **InstallShield Limited Edition**, and give your project a name.</span></span> <span data-ttu-id="e8ef3-124">(İstenirse, indirin, yükleyin ve InstallShield etkinleştirin.)</span><span class="sxs-lookup"><span data-stu-id="e8ef3-124">(If prompted, download, install, and activate InstallShield.)</span></span>  
  
3.  <span data-ttu-id="e8ef3-125">Kurulum ve dağıtım projenizin genel yapılandırma proje Yardımcısı'nda kullanarak ya da gerçekleştirmek **Çözüm Gezgini**, veya alt adımlar numaralı adımlarını seçerek **Çözüm Gezgini**. GAC derlemeleri ekleyecekseniz yaptığınız gibi ayarlarınızı yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-125">Perform the general configuration of your setup and deployment project either by using the Project Assistant in **Solution Explorer**, or by choosing the substeps of the numbered steps in the **Solution Explorer**.Configure your setup as you would if you were not adding assemblies to the GAC.</span></span>  
  
4.  <span data-ttu-id="e8ef3-126">Bir derlemeyi GAC'ye ekleme işlemini başlatmak için tercih **dosyaları**, altında olduğu **uygulama verilerini belirtin** adımını **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-126">To begin the process of adding an assembly to the GAC, choose **Files**, which is under the **Specify Application Data** step in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="e8ef3-127">İçinde **hedef bilgisayarın klasörleri** bölmesinde için kısayol menüsünü açın **hedef bilgisayar**ve ardından **önceden tanımlanmış klasörünü göster**, **[ GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-127">In the **Destination computer's folders** pane, open the shortcut menu for **Destination Computer**, and then choose **Show Predefined Folder**, **[GlobalAssemblyCache]**.</span></span>  
  
6.  <span data-ttu-id="e8ef3-128">Çözümde yer alan ve genel derleme önbelleğine yüklemek istediğiniz bir derlemeyi içeren her bir proje için:</span><span class="sxs-lookup"><span data-stu-id="e8ef3-128">For each project in the solution that contains an assembly that you want to install in the global assembly cache:</span></span>  
  
    1.  <span data-ttu-id="e8ef3-129">İçinde **bilgisayarın klasörleri kaynak** bölmesinde projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-129">In the **Source computer's folders** pane, choose the project.</span></span>  
  
    2.  <span data-ttu-id="e8ef3-130">İçinde **hedef bilgisayarın klasörleri** bölmesinde seçin **[GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-130">In the **Destination computer's folders** pane, choose **[GlobalAssemblyCache]**.</span></span>  
  
    3.  <span data-ttu-id="e8ef3-131">İçinde **bilgisayarın dosyalarını kaynağı** bölmesinde seçin **birincil çıktı** *< project_name >*.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-131">In the **Source computer's files** pane, choose **Primary output from** *<project_name>*.</span></span>  
  
    4.  <span data-ttu-id="e8ef3-132">Adım c dosyasında sürükleyin **hedef bilgisayarın dosyaları** bölmesinde (veya **kopyalama** ve **Yapıştır** dosyanın kısayol menüsünden komutları).</span><span class="sxs-lookup"><span data-stu-id="e8ef3-132">Drag the file in step c to the **Destination computer's files** pane (or use the **Copy** and **Paste** commands from the file's shortcut menu).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ef3-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e8ef3-133">See Also</span></span>  
 [<span data-ttu-id="e8ef3-134">Derlemeler ve genel derleme önbelleği ile çalışma</span><span class="sxs-lookup"><span data-stu-id="e8ef3-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="e8ef3-135">Nasıl yapılır: bir derlemeyi genel derleme önbelleğinden kaldırma</span><span class="sxs-lookup"><span data-stu-id="e8ef3-135">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [<span data-ttu-id="e8ef3-136">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="e8ef3-136">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [<span data-ttu-id="e8ef3-137">Nasıl yapılır: bir derlemeyi tanımlayıcı adla imzalama</span><span class="sxs-lookup"><span data-stu-id="e8ef3-137">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="e8ef3-138">Windows Installer dağıtımı</span><span class="sxs-lookup"><span data-stu-id="e8ef3-138">Windows Installer Deployment</span></span>](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)
