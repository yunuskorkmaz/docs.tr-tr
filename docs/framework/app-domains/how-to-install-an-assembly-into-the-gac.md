---
title: 'Nasıl yapılır: Bir derlemeyi genel derleme önbelleğine yükleme'
ms.date: 02/05/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 233a7803cb59f9bfeac15d293dc3fb5a0db449c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674993"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="9b7fa-102">Nasıl yapılır: Bir derlemeyi genel derleme önbelleğine yükleme</span><span class="sxs-lookup"><span data-stu-id="9b7fa-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="9b7fa-103">Bazı uygulamalar paylaşan derlemeleri genel bütünleştirilmiş kod önbelleği (GAC) depolar.</span><span class="sxs-lookup"><span data-stu-id="9b7fa-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="9b7fa-104">Bütünleştirilmiş kod içine yüklemek [genel derleme önbelleği](gac.md) aşağıdaki bileşenlerden biri ile:</span><span class="sxs-lookup"><span data-stu-id="9b7fa-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span> 
- [<span data-ttu-id="9b7fa-105">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="9b7fa-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="9b7fa-106">Genel Derleme Önbelleği Aracı</span><span class="sxs-lookup"><span data-stu-id="9b7fa-106">Global assembly cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="9b7fa-107">Yalnızca katı adlı derlemeler GAC içine yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b7fa-107">You can install only strong-named assemblies into the GAC.</span></span> <span data-ttu-id="9b7fa-108">Bir katı adlı derleme oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir derlemeyi katı bir adla imzalamak](how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="9b7fa-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](how-to-sign-an-assembly-with-a-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="9b7fa-109">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="9b7fa-109">Windows Installer</span></span>

<span data-ttu-id="9b7fa-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), Windows yükleme altyapısı, derlemeleri genel bütünleştirilmiş kod önbelleğine eklemek için önerilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="9b7fa-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="9b7fa-111">Windows Installer, derlemeleri genel derleme önbelleğini ve diğer avantajlar başvuru sayımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b7fa-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="9b7fa-112">İçin Windows Installer bir yükleyici paketi oluşturmak için kullanın [WiX toolset uzantı Visual Studio 2017 için](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="9b7fa-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="9b7fa-113">Genel Derleme Önbelleği Aracı</span><span class="sxs-lookup"><span data-stu-id="9b7fa-113">Global assembly cache tool</span></span>

<span data-ttu-id="9b7fa-114">Kullanabileceğiniz [Genel Derleme Önbelleği aracını (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) derlemeleri genel derleme önbelleğine ekleme ve genel derleme önbelleğinin içeriğini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="9b7fa-114">You can use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="9b7fa-115">*Gacutil.exe* yalnızca geliştirme amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="9b7fa-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="9b7fa-116">Genel bütünleştirilmiş kod önbelleğine üretim derlemeleri yüklemek için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="9b7fa-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="9b7fa-117">Kullanmaya ilişkin sözdizimini *gacutil.exe* bir derlemeyi GAC'ye yüklemek için şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="9b7fa-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```console
gacutil -i <assembly name>
```

<span data-ttu-id="9b7fa-118">Bu komutta  *\<derleme adı >* genel bütünleştirilmiş kod önbelleğine yüklenecek derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="9b7fa-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="9b7fa-119">Varsa *gacutil.exe* kullanın, sistem yolunda değil [VS için geliştirici komut istemi  *\<sürüm >*](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9b7fa-119">If *gacutil.exe* isn't in your system path, use the [Developer Command Prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="9b7fa-120">Aşağıdaki örnek, dosya adı ile bir derlemeyi yükler *hello.dll* genel bütünleştirilmiş kod önbelleğine.</span><span class="sxs-lookup"><span data-stu-id="9b7fa-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```console
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="9b7fa-121">.NET Framework'ün önceki sürümlerindeki *Shfusion.dll* Windows kabuk uzantısı derlemeleri dosya Gezgini'nde sürükleyerek yüklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9b7fa-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="9b7fa-122">.NET Framework 4 ile başlayarak *Shfusion.dll* kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="9b7fa-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b7fa-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b7fa-123">See also</span></span>

- [<span data-ttu-id="9b7fa-124">Derlemeler ve genel derleme önbelleği ile çalışma</span><span class="sxs-lookup"><span data-stu-id="9b7fa-124">Working with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="9b7fa-125">Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırma</span><span class="sxs-lookup"><span data-stu-id="9b7fa-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="9b7fa-126">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="9b7fa-126">Gacutil.exe (Global assembly cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="9b7fa-127">Nasıl yapılır: Derlemeyi tanımlayıcı bir adla imzalama</span><span class="sxs-lookup"><span data-stu-id="9b7fa-127">How to: Sign an assembly with a strong name</span></span>](how-to-sign-an-assembly-with-a-strong-name.md)
