---
title: Bir derlemeyi GAC içine yükleme
ms.date: 09/20/2018
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
ms.openlocfilehash: d365ac77fe6cd7fc4fca36705729ec12b06d6830
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584587"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="2456f-102">Nasıl yapılır: bir derlemeyi genel derleme önbelleğine yükleme</span><span class="sxs-lookup"><span data-stu-id="2456f-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="2456f-103">Bir katı adlı derlemeyi genel bütünleştirilmiş kod önbelleğine (GAC) yüklemenin iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="2456f-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2456f-104">Yalnızca katı adlı derlemeler GAC içine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="2456f-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="2456f-105">Bir katı adlı derleme oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi tanımlayıcı bir adla imzalamak](how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="2456f-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](how-to-sign-an-assembly-with-a-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="2456f-106">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="2456f-106">Windows Installer</span></span>

<span data-ttu-id="2456f-107">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), Windows yükleme altyapısı, derlemeleri genel bütünleştirilmiş kod önbelleğine eklemek için önerilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="2456f-107">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="2456f-108">Windows Installer, derlemeleri genel derleme önbelleğini ve diğer avantajlar başvuru sayımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2456f-108">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="2456f-109">Kullanabileceğiniz [WiX Toolset uzantı Visual Studio 2017 için](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) Windows Yükleyicisi için bir yükleyici paketi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="2456f-109">You can use the [WiX Toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) to create an installer package for Windows Installer.</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="2456f-110">Genel Derleme Önbelleği Aracı</span><span class="sxs-lookup"><span data-stu-id="2456f-110">Global assembly cache tool</span></span>

<span data-ttu-id="2456f-111">Kullanabileceğiniz [Genel Derleme Önbelleği aracını (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) genel derleme önbelleğine katı adlı derlemeler eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="2456f-111">You can use the [Global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="2456f-112">Gacutil.exe yalnızca geliştirme amaçlıdır ve genel bütünleştirilmiş kod önbelleğine üretim derlemeleri yüklemek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2456f-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="2456f-113">Gacutil sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2456f-113">The syntax for gacutil is as follows:</span></span>

```shell
gacutil -i <assembly name>
```

<span data-ttu-id="2456f-114">Bu komutta *derleme adı* genel bütünleştirilmiş kod önbelleğine yüklenecek derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="2456f-114">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="2456f-115">Aşağıdaki örnek, dosya adı ile bir derlemeyi yükler `hello.dll` genel bütünleştirilmiş kod önbelleğine.</span><span class="sxs-lookup"><span data-stu-id="2456f-115">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>

```shell
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="2456f-116">Önceki .NET Framework sürümlerinde, Shfusion.dll Windows kabuk uzantısı, bunları sürükleyerek derlemeleri yüklemek etkin **dosya Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="2456f-116">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in **File Explorer**.</span></span> <span data-ttu-id="2456f-117">.NET Framework 4 ile başlayarak, Shfusion.dll kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="2456f-117">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="2456f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2456f-118">See also</span></span>

- [<span data-ttu-id="2456f-119">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="2456f-119">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="2456f-120">Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğinden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="2456f-120">How to: Remove an Assembly from the Global Assembly Cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="2456f-121">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="2456f-121">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="2456f-122">Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="2456f-122">How to: Sign an Assembly with a Strong Name</span></span>](how-to-sign-an-assembly-with-a-strong-name.md)