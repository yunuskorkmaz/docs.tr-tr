---
title: 'Nasıl yapilir: Derlemeyi genel derleme önbelleğine yükleme'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 64878a795a7c5b790c8991064e32b82505685c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155569"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="d02f1-102">Nasıl yapilir: Derlemeyi genel derleme önbelleğine yükleme</span><span class="sxs-lookup"><span data-stu-id="d02f1-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="d02f1-103">Genel derleme önbelleği (GAC), çeşitli uygulamaların paylaştığı derlemeleri depolar.</span><span class="sxs-lookup"><span data-stu-id="d02f1-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="d02f1-104">Aşağıdaki bileşenlerden biriyle bir derlemeyi [genel montaj önbelleğine](gac.md) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="d02f1-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="d02f1-105">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="d02f1-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="d02f1-106">Genel Montaj Önbellek aracı</span><span class="sxs-lookup"><span data-stu-id="d02f1-106">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="d02f1-107">Genel derleme önbelleğine yalnızca güçlü adlandırılmış derlemeler yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d02f1-107">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="d02f1-108">Güçlü adlandırılmış bir derlemenin nasıl oluşturulabildiğini öğrenmek için [bkz.](../../standard/assembly/sign-strong-name.md)</span><span class="sxs-lookup"><span data-stu-id="d02f1-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="d02f1-109">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="d02f1-109">Windows Installer</span></span>

<span data-ttu-id="d02f1-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), Windows yükleme motoru, genel derleme önbelleğine derlemeler eklemek için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="d02f1-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="d02f1-111">Windows Installer, genel derleme önbelleğindeki derlemelerin başvuru sayımını ve diğer avantajları sağlar.</span><span class="sxs-lookup"><span data-stu-id="d02f1-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="d02f1-112">Windows Installer için yükleyici paketi oluşturmak [için Visual Studio 2017 için WiX araç seti uzantısını](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)kullanın.</span><span class="sxs-lookup"><span data-stu-id="d02f1-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="d02f1-113">Genel Montaj Önbellek aracı</span><span class="sxs-lookup"><span data-stu-id="d02f1-113">Global Assembly Cache tool</span></span>

<span data-ttu-id="d02f1-114">[.NET Global Assembly Cache yardımcı programını (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) genel derleme önbelleğine derlemeler eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d02f1-114">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="d02f1-115">*Gacutil.exe* sadece geliştirme amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="d02f1-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="d02f1-116">Üretim derlemelerini genel derleme önbelleğine yüklemek için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="d02f1-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="d02f1-117">GAC bir derleme yüklemek için *gacutil.exe* kullanmak için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d02f1-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="d02f1-118">Bu komutta, \* \<derleme adı>,\* genel derleme önbelleğine yüklenmesi gereken derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="d02f1-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="d02f1-119">*gacutil.exe* sistem yolunuzda değilse, [VS \* \<sürümü>\* için Geliştirici komut istemini ](../tools/developer-command-prompt-for-vs.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="d02f1-119">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="d02f1-120">Aşağıdaki örnek, genel derleme önbelleğine dosya adı *hello.dll* içeren bir derleme yükler.</span><span class="sxs-lookup"><span data-stu-id="d02f1-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="d02f1-121">.NET Framework'ün önceki sürümlerinde, *Shfusion.dll* Windows kabuk uzantısı derlemeleri Dosya Gezgini'ne sürükleyerek yüklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d02f1-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="d02f1-122">.NET Framework 4 ile başlayarak, *Shfusion.dll* eskidir.</span><span class="sxs-lookup"><span data-stu-id="d02f1-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="d02f1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d02f1-123">See also</span></span>

- [<span data-ttu-id="d02f1-124">Derlemeler ve genel montaj önbelleği yle çalışma</span><span class="sxs-lookup"><span data-stu-id="d02f1-124">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="d02f1-125">Nasıl yapilir: Derlemeyi genel montaj önbelleğinden kaldırma</span><span class="sxs-lookup"><span data-stu-id="d02f1-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="d02f1-126">Gacutil.exe (Küresel Montaj Önbellek aracı)</span><span class="sxs-lookup"><span data-stu-id="d02f1-126">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="d02f1-127">Nasıl yapilir: Güçlü bir ada sahip bir derlemeyi imzalama</span><span class="sxs-lookup"><span data-stu-id="d02f1-127">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
