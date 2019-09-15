---
title: 'Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler'
ms.date: 08/20/2019
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
ms.openlocfilehash: de5ae03ab885c4368e39b6339b5a14d1082e6df5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972937"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="2b8f3-102">Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler</span><span class="sxs-lookup"><span data-stu-id="2b8f3-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="2b8f3-103">Genel bütünleştirilmiş kod önbelleği (GAC), birkaç uygulamanın paylaştığı derlemeleri depolar.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="2b8f3-104">Aşağıdaki bileşenlerden biriyle bir derlemeyi [genel bütünleştirilmiş kod önbelleğine](gac.md) yükler:</span><span class="sxs-lookup"><span data-stu-id="2b8f3-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span> 

- [<span data-ttu-id="2b8f3-105">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="2b8f3-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="2b8f3-106">Genel derleme önbelleği aracı</span><span class="sxs-lookup"><span data-stu-id="2b8f3-106">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="2b8f3-107">Genel bütünleştirilmiş kod önbelleğine yalnızca tanımlayıcı adlı derlemeler yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-107">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="2b8f3-108">Tanımlayıcı adlı bütünleştirilmiş kod oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir derlemeyi güçlü bir adla](../../standard/assembly/sign-strong-name.md)imzalayın.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="2b8f3-109">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="2b8f3-109">Windows Installer</span></span>

<span data-ttu-id="2b8f3-110">Windows yükleme altyapısı [Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), genel derleme önbelleğine derlemeler eklemenin önerilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="2b8f3-111">Windows Installer, genel derleme önbelleğindeki derlemelerin ve diğer avantajlardan başvuru saymasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="2b8f3-112">Windows Installer için bir yükleyici paketi oluşturmak için, [Visual Studio 2017 Için Wix araç takımı uzantısını](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="2b8f3-113">Genel Derleme Önbelleği aracı</span><span class="sxs-lookup"><span data-stu-id="2b8f3-113">Global Assembly Cache tool</span></span>

<span data-ttu-id="2b8f3-114">Genel bütünleştirilmiş kod önbelleğine derleme eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için [.NET genel derleme önbelleği yardımcı programını (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-114">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="2b8f3-115">*Gacutil. exe* yalnızca geliştirme amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="2b8f3-116">Bu uygulamayı, genel derleme önbelleğine üretim derlemeleri yüklemek için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="2b8f3-117">GAC 'de bir derlemeyi yüklemek için *Gacutil. exe* ' yi kullanma söz dizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2b8f3-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="2b8f3-118">Bu komutta,  *\<derleme adı >* , genel derleme önbelleğine yüklenecek derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="2b8f3-119">*Gacutil. exe* dosyası sistem yolunuzda değilse, [vs  *\<sürüm >* için geliştirici komut istemi](../tools/developer-command-prompt-for-vs.md)' ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-119">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="2b8f3-120">Aşağıdaki örnek, *Hello. dll* dosya adına sahip bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="2b8f3-121">.NET Framework önceki sürümlerinde, *Shfusion. dll* Windows kabuğu uzantısı, derlemeleri dosya Gezgini 'ne sürükleyerek yüklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="2b8f3-122">.NET Framework 4 ' ten başlayarak *Shfusion. dll* artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b8f3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b8f3-123">See also</span></span>

- [<span data-ttu-id="2b8f3-124">Derlemeler ve genel derleme önbelleği ile çalışma</span><span class="sxs-lookup"><span data-stu-id="2b8f3-124">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="2b8f3-125">Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırma</span><span class="sxs-lookup"><span data-stu-id="2b8f3-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="2b8f3-126">Gacutil. exe (genel derleme önbelleği aracı)</span><span class="sxs-lookup"><span data-stu-id="2b8f3-126">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="2b8f3-127">Nasıl yapılır: Bir derlemeyi güçlü bir adla imzala</span><span class="sxs-lookup"><span data-stu-id="2b8f3-127">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
