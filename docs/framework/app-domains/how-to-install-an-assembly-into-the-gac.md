---
title: 'Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğine Yükleme'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c3bd568cf504125bc99801815d08764417b42cd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469004"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="d68c9-102">Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğine Yükleme</span><span class="sxs-lookup"><span data-stu-id="d68c9-102">How to: Install an Assembly into the Global Assembly Cache</span></span>
<span data-ttu-id="d68c9-103">Bir katı adlı derlemeyi genel derleme önbelleğine (GAC) yüklemenin iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="d68c9-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC):</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d68c9-104">Yalnızca katı adlı derlemeler GAC içine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d68c9-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="d68c9-105">Bir katı adlı derleme oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi tanımlayıcı bir adla imzalamak](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="d68c9-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
-   <span data-ttu-id="d68c9-106">Kullanarak [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span><span class="sxs-lookup"><span data-stu-id="d68c9-106">Using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span>  
  
     <span data-ttu-id="d68c9-107">Bunu, Visual Studio 2012 ve Visual Studio 2013'te bir InstallShield Limited Edition Projesi oluşturarak yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="d68c9-107">You do this in Visual Studio 2012 and Visual Studio 2013 by creating an InstallShield Limited Edition Project.</span></span>  
  
     <span data-ttu-id="d68c9-108">Bu, genel derleme önbelleğine derlemeler eklemenin önerilen ve en yaygın yoludur.</span><span class="sxs-lookup"><span data-stu-id="d68c9-108">This is the recommended and most common way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="d68c9-109">Yükleyici, genel derleme önbelleğindeki derlemelerin referans amaçlı sayımını ve başka yararları sağlar.</span><span class="sxs-lookup"><span data-stu-id="d68c9-109">The installer provides reference counting of assemblies in the global assembly cache, plus other benefits.</span></span>  
  
-   <span data-ttu-id="d68c9-110">Kullanarak [Genel Derleme Önbelleği aracını (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d68c9-110">Using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
     <span data-ttu-id="d68c9-111">Genel derleme önbelleğine katı adlı derlemeler eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için Gacutil.exe'yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d68c9-111">You can use Gacutil.exe to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d68c9-112">Gacutil.exe yalnızca geliştirme amaçlıdır ve genel bütünleştirilmiş kod önbelleğine üretim derlemeleri yüklemek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d68c9-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d68c9-113">Önceki .NET Framework sürümlerinde, Shfusion.dll Windows kabuk uzantısı derlemeleri dosya Gezgini'nde sürükleyerek yüklemenize olanak etkin.</span><span class="sxs-lookup"><span data-stu-id="d68c9-113">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in File Explorer.</span></span> <span data-ttu-id="d68c9-114">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="d68c9-114">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a><span data-ttu-id="d68c9-115">Genel Derleme Önbelleği aracını (Gacutil.exe) kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="d68c9-115">To use the Global Assembly Cache tool (Gacutil.exe)</span></span>  
  
1.  <span data-ttu-id="d68c9-116">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="d68c9-116">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="d68c9-117">**Gacutil -i** \< *derleme adı*></span><span class="sxs-lookup"><span data-stu-id="d68c9-117">**gacutil -i** \<*assembly name*></span></span>  
  
     <span data-ttu-id="d68c9-118">Bu komutta *derleme adı* genel bütünleştirilmiş kod önbelleğine yüklenecek derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="d68c9-118">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>  
  
 <span data-ttu-id="d68c9-119">Aşağıdaki örnek, dosya adı ile bir derlemeyi yükler `hello.dll` genel bütünleştirilmiş kod önbelleğine.</span><span class="sxs-lookup"><span data-stu-id="d68c9-119">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>  
  
```  
gacutil -i hello.dll  
```  
  
 <span data-ttu-id="d68c9-120">Daha fazla bilgi için [Genel Derleme Önbelleği aracını (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d68c9-120">For more information, see [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
### <a name="to-use-an-installshield-limited-edition-project"></a><span data-ttu-id="d68c9-121">Bir InstallShield Limited Edition Projesi'ni kullanmak için</span><span class="sxs-lookup"><span data-stu-id="d68c9-121">To use an InstallShield Limited Edition Project</span></span>  
  
1.  <span data-ttu-id="d68c9-122">Çözümünüz için kısayol menüsünü açıp ardından çözümünüze bir kurulum ve dağıtım paketi ekleyin **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="d68c9-122">Add a setup and deployment package to your solution by opening the shortcut menu for your solution, and then choosing **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="d68c9-123">İçinde **Yeni Proje Ekle** iletişim kutusundaki **yüklü** klasörü seçin **diğer proje türleri**, **Kurulum ve dağıtım**, **InstallShield Limited Edition**ve projenize bir ad verin.</span><span class="sxs-lookup"><span data-stu-id="d68c9-123">In the **Add New Project** dialog box, in the **Installed** folder, choose **Other Project Types**,  **Setup and Deployment**, **InstallShield Limited Edition**, and give your project a name.</span></span> <span data-ttu-id="d68c9-124">(İstenirse, indirin, yükleyin ve InstallShield etkinleştirin.)</span><span class="sxs-lookup"><span data-stu-id="d68c9-124">(If prompted, download, install, and activate InstallShield.)</span></span>  
  
3.  <span data-ttu-id="d68c9-125">Proje Asistanı kullanarak kurulum ve dağıtım projenizin genel yapılandırmasını gerçekleştirin **Çözüm Gezgini**, veya alt adımların numaralı adımları seçerek **Çözüm Gezgini**. Derlemeleri GAC'ye eklemekte değil, yaptığınız gibi kurulumunuzu yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d68c9-125">Perform the general configuration of your setup and deployment project either by using the Project Assistant in **Solution Explorer**, or by choosing the substeps of the numbered steps in the **Solution Explorer**.Configure your setup as you would if you were not adding assemblies to the GAC.</span></span>  
  
4.  <span data-ttu-id="d68c9-126">GAC'ye bir derleme ekleme işlemine başlamak için seçin **dosyaları**, altında olduğu **uygulama verilerini belirtin** adımı **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="d68c9-126">To begin the process of adding an assembly to the GAC, choose **Files**, which is under the **Specify Application Data** step in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="d68c9-127">İçinde **hedef bilgisayarın klasörleri** bölmesinde, kısayol menüsünü açın **hedef bilgisayar**ve ardından **önceden tanımlanmış klasörü Göster**, **[ GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="d68c9-127">In the **Destination computer's folders** pane, open the shortcut menu for **Destination Computer**, and then choose **Show Predefined Folder**, **[GlobalAssemblyCache]**.</span></span>  
  
6.  <span data-ttu-id="d68c9-128">Çözümde yer alan ve genel derleme önbelleğine yüklemek istediğiniz bir derlemeyi içeren her bir proje için:</span><span class="sxs-lookup"><span data-stu-id="d68c9-128">For each project in the solution that contains an assembly that you want to install in the global assembly cache:</span></span>  
  
    1.  <span data-ttu-id="d68c9-129">İçinde **kaynak bilgisayarın klasörleri** bölmesinde projeyi seçin.</span><span class="sxs-lookup"><span data-stu-id="d68c9-129">In the **Source computer's folders** pane, choose the project.</span></span>  
  
    2.  <span data-ttu-id="d68c9-130">İçinde **hedef bilgisayarın klasörleri** bölmesinde seçin **; [GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="d68c9-130">In the **Destination computer's folders** pane, choose **[GlobalAssemblyCache]**.</span></span>  
  
    3.  <span data-ttu-id="d68c9-131">İçinde **kaynak bilgisayarın dosyaları** bölmesinde seçin **birincil çıktıyı** *< project_name >*.</span><span class="sxs-lookup"><span data-stu-id="d68c9-131">In the **Source computer's files** pane, choose **Primary output from** *<project_name>*.</span></span>  
  
    4.  <span data-ttu-id="d68c9-132">Adım C'deki dosyayı sürükleyin **hedef bilgisayarın dosyaları** bölmesinde (veya **kopyalama** ve **Yapıştır** komutları dosyanın kısayol menüsünden).</span><span class="sxs-lookup"><span data-stu-id="d68c9-132">Drag the file in step c to the **Destination computer's files** pane (or use the **Copy** and **Paste** commands from the file's shortcut menu).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d68c9-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d68c9-133">See Also</span></span>  
 [<span data-ttu-id="d68c9-134">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="d68c9-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="d68c9-135">Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğinden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="d68c9-135">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [<span data-ttu-id="d68c9-136">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="d68c9-136">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [<span data-ttu-id="d68c9-137">Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="d68c9-137">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="d68c9-138">Windows Installer dağıtımı</span><span class="sxs-lookup"><span data-stu-id="d68c9-138">Windows Installer Deployment</span></span>](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
