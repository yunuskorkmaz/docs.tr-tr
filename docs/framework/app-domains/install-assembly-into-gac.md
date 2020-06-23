---
title: 'Nasıl yapılır: Bir bütünleştirilmiş kodu genel derleme önbelleğine yükleme'
description: Bir derlemeyi, .NET 'teki genel derleme önbelleği 'ne (GAC) yükleyerek birçok uygulama tarafından paylaşılabilir. Windows Installer veya GAC yardımcı programını kullanın.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 08a5475d74327265f28b65676ae56be15afb57d3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104660"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="b95eb-104">Nasıl yapılır: Bir bütünleştirilmiş kodu genel derleme önbelleğine yükleme</span><span class="sxs-lookup"><span data-stu-id="b95eb-104">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="b95eb-105">Genel bütünleştirilmiş kod önbelleği (GAC), birkaç uygulamanın paylaştığı derlemeleri depolar.</span><span class="sxs-lookup"><span data-stu-id="b95eb-105">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="b95eb-106">Aşağıdaki bileşenlerden biriyle bir derlemeyi [genel bütünleştirilmiş kod önbelleğine](gac.md) yükler:</span><span class="sxs-lookup"><span data-stu-id="b95eb-106">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="b95eb-107">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="b95eb-107">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="b95eb-108">Genel derleme önbelleği aracı</span><span class="sxs-lookup"><span data-stu-id="b95eb-108">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="b95eb-109">Genel bütünleştirilmiş kod önbelleğine yalnızca tanımlayıcı adlı derlemeler yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b95eb-109">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="b95eb-110">Tanımlayıcı adlı bütünleştirilmiş kod oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: derlemeyi güçlü bir adla imzalama](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="b95eb-110">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="b95eb-111">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="b95eb-111">Windows Installer</span></span>

<span data-ttu-id="b95eb-112">Windows yükleme altyapısı [Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), genel derleme önbelleğine derlemeler eklemenin önerilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="b95eb-112">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="b95eb-113">Windows Installer, genel derleme önbelleğindeki derlemelerin ve diğer avantajlardan başvuru saymasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b95eb-113">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="b95eb-114">Windows Installer için bir yükleyici paketi oluşturmak için, [Visual Studio 2017 Için Wix araç takımı uzantısını](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)kullanın.</span><span class="sxs-lookup"><span data-stu-id="b95eb-114">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="b95eb-115">Genel derleme önbelleği aracı</span><span class="sxs-lookup"><span data-stu-id="b95eb-115">Global Assembly Cache tool</span></span>

<span data-ttu-id="b95eb-116">Genel derleme önbelleğine derleme eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için [.NET genel derleme önbelleği yardımcı programını (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b95eb-116">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b95eb-117">*Gacutil.exe* yalnızca geliştirme amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="b95eb-117">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="b95eb-118">Bu uygulamayı, genel derleme önbelleğine üretim derlemeleri yüklemek için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b95eb-118">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="b95eb-119">GAC 'de bir derlemeyi yüklemek için *gacutil.exe* kullanmak için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b95eb-119">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="b95eb-120">Bu komutta, *\<assembly name>* genel derleme önbelleğine yüklenecek derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="b95eb-120">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="b95eb-121">*gacutil.exe* sistem yolunuzda yoksa, [vs *\<version>* için geliştirici komut istemi ](../tools/developer-command-prompt-for-vs.md)' ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="b95eb-121">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="b95eb-122">Aşağıdaki örnek, *hello.dll* dosya adı olan bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b95eb-122">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="b95eb-123">.NET Framework önceki sürümlerinde, *Shfusion.dll* Windows kabuğu uzantısı, derlemeleri dosya Gezgini 'ne sürükleyerek yüklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b95eb-123">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="b95eb-124">.NET Framework 4 ' ten başlayarak *Shfusion.dll* artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b95eb-124">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="b95eb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b95eb-125">See also</span></span>

- [<span data-ttu-id="b95eb-126">Derlemeler ve genel derleme önbelleği ile çalışma</span><span class="sxs-lookup"><span data-stu-id="b95eb-126">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="b95eb-127">Nasıl yapılır: genel bütünleştirilmiş kod önbelleğinden bir derlemeyi kaldırma</span><span class="sxs-lookup"><span data-stu-id="b95eb-127">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="b95eb-128">Gacutil.exe (genel derleme önbelleği aracı)</span><span class="sxs-lookup"><span data-stu-id="b95eb-128">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="b95eb-129">Nasıl yapılır: bir derlemeyi güçlü bir adla Imzalama</span><span class="sxs-lookup"><span data-stu-id="b95eb-129">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
