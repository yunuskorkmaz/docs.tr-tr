---
title: 'Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler'
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
ms.openlocfilehash: 8e2d051cda9861da1af2caa65160b6e753b24bd1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926508"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="7f040-102">Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler</span><span class="sxs-lookup"><span data-stu-id="7f040-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="7f040-103">Genel bütünleştirilmiş kod önbelleği (GAC), birkaç uygulamanın paylaştığı derlemeleri depolar.</span><span class="sxs-lookup"><span data-stu-id="7f040-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="7f040-104">Aşağıdaki bileşenlerden biriyle bir derlemeyi [genel bütünleştirilmiş kod önbelleğine](gac.md) yükler:</span><span class="sxs-lookup"><span data-stu-id="7f040-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span> 

- [<span data-ttu-id="7f040-105">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="7f040-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="7f040-106">Genel derleme önbelleği aracı</span><span class="sxs-lookup"><span data-stu-id="7f040-106">Global assembly cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="7f040-107">GAC 'ye yalnızca tanımlayıcı adlı derlemeler yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f040-107">You can install only strong-named assemblies into the GAC.</span></span> <span data-ttu-id="7f040-108">Tanımlayıcı adlı bütünleştirilmiş kod oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir derlemeyi güçlü bir adla](how-to-sign-an-assembly-with-a-strong-name.md)imzalayın.</span><span class="sxs-lookup"><span data-stu-id="7f040-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](how-to-sign-an-assembly-with-a-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="7f040-109">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="7f040-109">Windows Installer</span></span>

<span data-ttu-id="7f040-110">Windows yükleme altyapısı [Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), genel derleme önbelleğine derlemeler eklemenin önerilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="7f040-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="7f040-111">Windows Installer, genel derleme önbelleğindeki derlemelerin ve diğer avantajlardan başvuru saymasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f040-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="7f040-112">Windows Installer için bir yükleyici paketi oluşturmak için, [Visual Studio 2017 Için Wix araç takımı uzantısını](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f040-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="7f040-113">Genel derleme önbelleği aracı</span><span class="sxs-lookup"><span data-stu-id="7f040-113">Global assembly cache tool</span></span>

<span data-ttu-id="7f040-114">Genel bütünleştirilmiş kod önbelleğine derleme eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için [genel derleme önbelleği aracını (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f040-114">You can use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7f040-115">*Gacutil. exe* yalnızca geliştirme amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="7f040-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="7f040-116">Bu uygulamayı, genel derleme önbelleğine üretim derlemeleri yüklemek için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="7f040-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="7f040-117">GAC 'de bir derlemeyi yüklemek için *Gacutil. exe* ' yi kullanma söz dizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7f040-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```console
gacutil -i <assembly name>
```

<span data-ttu-id="7f040-118">Bu komutta,  *\<derleme adı >* , genel derleme önbelleğine yüklenecek derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="7f040-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="7f040-119">*Gacutil. exe* dosyası sistem yolunuzda değilse, [vs  *\<sürüm >* için geliştirici komut istemi](../tools/developer-command-prompt-for-vs.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f040-119">If *gacutil.exe* isn't in your system path, use the [Developer Command Prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="7f040-120">Aşağıdaki örnek, *Hello. dll* dosya adına sahip bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler.</span><span class="sxs-lookup"><span data-stu-id="7f040-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```console
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="7f040-121">.NET Framework önceki sürümlerinde, *Shfusion. dll* Windows kabuğu uzantısı, derlemeleri dosya Gezgini 'ne sürükleyerek yüklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f040-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="7f040-122">.NET Framework 4 ' ten başlayarak *Shfusion. dll* artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="7f040-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f040-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f040-123">See also</span></span>

- [<span data-ttu-id="7f040-124">Derlemeler ve genel derleme önbelleği ile çalışma</span><span class="sxs-lookup"><span data-stu-id="7f040-124">Working with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="7f040-125">Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırma</span><span class="sxs-lookup"><span data-stu-id="7f040-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="7f040-126">Gacutil. exe (genel derleme önbelleği aracı)</span><span class="sxs-lookup"><span data-stu-id="7f040-126">Gacutil.exe (Global assembly cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="7f040-127">Nasıl yapılır: Bir derlemeyi güçlü bir adla imzala</span><span class="sxs-lookup"><span data-stu-id="7f040-127">How to: Sign an assembly with a strong name</span></span>](how-to-sign-an-assembly-with-a-strong-name.md)
