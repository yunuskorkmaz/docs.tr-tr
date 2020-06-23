---
title: 'Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğinden Kaldırma'
description: Genel derleme önbelleği aracını (Gacutil.exe) veya Windows Installer kullanarak .NET 'teki genel derleme önbelleğinden bir derlemeyi kaldırmayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
ms.openlocfilehash: e3a596ea6029ded190c33032e96b601de9d4012d
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104769"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="c2942-103">Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğinden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="c2942-103">How to: Remove an Assembly from the Global Assembly Cache</span></span>

<span data-ttu-id="c2942-104">Bir derlemeyi genel bütünleştirilmiş kod önbelleğinden (GAC) kaldırmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="c2942-104">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>

- <span data-ttu-id="c2942-105">[Genel derleme önbelleği aracını (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md)kullanarak.</span><span class="sxs-lookup"><span data-stu-id="c2942-105">By using the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="c2942-106">Geliştirme ve test sırasında GAC 'ye yerleştirdiğiniz derlemeleri kaldırmak için bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2942-106">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>

- <span data-ttu-id="c2942-107">[Windows Installer](/windows/desktop/Msi/windows-installer-portal)kullanarak.</span><span class="sxs-lookup"><span data-stu-id="c2942-107">By using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span> <span data-ttu-id="c2942-108">Yükleme paketlerini ve üretim sistemlerini test ederken derlemeleri kaldırmak için bu seçeneği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2942-108">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>

## <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="c2942-109">Gacutil.exe bir derlemeyi kaldırma</span><span class="sxs-lookup"><span data-stu-id="c2942-109">Removing an assembly with Gacutil.exe</span></span>

<span data-ttu-id="c2942-110">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="c2942-110">At the command prompt, type the following command:</span></span>

<span data-ttu-id="c2942-111">**Gacutil – u**\<*assembly name*></span><span class="sxs-lookup"><span data-stu-id="c2942-111">**gacutil –u** \<*assembly name*></span></span>

<span data-ttu-id="c2942-112">Bu komutta, *derleme adı* genel derleme önbelleğinden kaldırılacak derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="c2942-112">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>

> [!WARNING]
> <span data-ttu-id="c2942-113">Derlemenin bazı uygulamalar tarafından hala gerekli olabileceğinden, üretim sistemlerindeki derlemeleri kaldırmak için Gacutil.exe kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="c2942-113">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="c2942-114">Bunun yerine, GAC içinde yüklediği her derleme için başvuru sayısını tutan Windows Installer kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2942-114">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>

<span data-ttu-id="c2942-115">Aşağıdaki örnek, genel derleme önbelleğinden adlı bir derlemeyi kaldırır `hello.dll` :</span><span class="sxs-lookup"><span data-stu-id="c2942-115">The following example removes an assembly named `hello.dll` from the global assembly cache:</span></span>

```console
gacutil -u hello
```

## <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="c2942-116">Windows Installer bir derlemeyi kaldırma</span><span class="sxs-lookup"><span data-stu-id="c2942-116">Removing an assembly with Windows Installer</span></span>

<span data-ttu-id="c2942-117">**Denetim Masası**'ndaki **Programlar ve Özellikler** uygulamasında kaldırmak istediğiniz uygulamayı seçin.</span><span class="sxs-lookup"><span data-stu-id="c2942-117">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="c2942-118">Yükleme paketi GAC 'ye derlemeler yerleştirirse, Windows Installer başka bir uygulama tarafından kullanılmıyorsa, bu dosyaları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c2942-118">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>

> [!NOTE]
> <span data-ttu-id="c2942-119">Windows Installer GAC 'de yüklü derlemeler için bir başvuru sayısı tutar.</span><span class="sxs-lookup"><span data-stu-id="c2942-119">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="c2942-120">Bir derleme GAC 'den yalnızca başvuru sayısı sıfıra ulaştığında kaldırılır. Bu, bir Windows Installer paketi tarafından yüklenen herhangi bir uygulama tarafından kullanılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2942-120">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2942-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2942-121">See also</span></span>

- [<span data-ttu-id="c2942-122">Derlemeler ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="c2942-122">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="c2942-123">Nasıl yapılır: bir derlemeyi genel derleme önbelleğine yüklemek</span><span class="sxs-lookup"><span data-stu-id="c2942-123">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)
- [<span data-ttu-id="c2942-124">Gacutil.exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="c2942-124">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
