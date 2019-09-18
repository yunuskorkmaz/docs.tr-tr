---
title: 'Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğinden Kaldırma'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aa88cbc73415695a1545704a2ad8cab535f011e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053138"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="6ecfb-102">Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğinden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="6ecfb-102">How to: Remove an Assembly from the Global Assembly Cache</span></span>

<span data-ttu-id="6ecfb-103">Bir derlemeyi genel bütünleştirilmiş kod önbelleğinden (GAC) kaldırmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="6ecfb-103">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>

- <span data-ttu-id="6ecfb-104">[Genel derleme önbelleği aracını (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md)kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-104">By using the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="6ecfb-105">Geliştirme ve test sırasında GAC 'ye yerleştirdiğiniz derlemeleri kaldırmak için bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-105">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>

- <span data-ttu-id="6ecfb-106">[Windows Installer](/windows/desktop/Msi/windows-installer-portal)kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-106">By using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span> <span data-ttu-id="6ecfb-107">Yükleme paketlerini ve üretim sistemlerini test ederken derlemeleri kaldırmak için bu seçeneği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-107">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>

### <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="6ecfb-108">Gacutil. exe ile bir derlemeyi kaldırma</span><span class="sxs-lookup"><span data-stu-id="6ecfb-108">Removing an assembly with Gacutil.exe</span></span>

1. <span data-ttu-id="6ecfb-109">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="6ecfb-109">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="6ecfb-110">**Gacutil – u** *bütünleştirilmiş kod adı* \<></span><span class="sxs-lookup"><span data-stu-id="6ecfb-110">**gacutil –u** \<*assembly name*></span></span>

    <span data-ttu-id="6ecfb-111">Bu komutta, *derleme adı* genel derleme önbelleğinden kaldırılacak derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-111">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>

    > [!WARNING]
    > <span data-ttu-id="6ecfb-112">Derlemenin bazı uygulamalar için hala gerekli olabileceği için, üretim sistemlerindeki derlemeleri kaldırmak üzere Gacutil. exe ' yi kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-112">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="6ecfb-113">Bunun yerine, GAC içinde yüklediği her derleme için başvuru sayısını tutan Windows Installer kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-113">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>

 <span data-ttu-id="6ecfb-114">Aşağıdaki örnek, genel derleme önbelleğinden adlı `hello.dll` bir derlemeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-114">The following example removes an assembly named `hello.dll` from the global assembly cache.</span></span>

```
gacutil -u hello
```

### <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="6ecfb-115">Windows Installer bir derlemeyi kaldırma</span><span class="sxs-lookup"><span data-stu-id="6ecfb-115">Removing an assembly with Windows Installer</span></span>

1. <span data-ttu-id="6ecfb-116">**Denetim Masası**'ndaki **Programlar ve Özellikler** uygulamasında kaldırmak istediğiniz uygulamayı seçin.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-116">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="6ecfb-117">Yükleme paketi GAC 'ye derlemeler yerleştirirse, Windows Installer başka bir uygulama tarafından kullanılmıyorsa, bu dosyaları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-117">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6ecfb-118">Windows Installer GAC 'de yüklü derlemeler için bir başvuru sayısı tutar.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-118">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="6ecfb-119">Bir derleme GAC 'den yalnızca başvuru sayısı sıfıra ulaştığında kaldırılır. Bu, bir Windows Installer paketi tarafından yüklenen herhangi bir uygulama tarafından kullanılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-119">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ecfb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ecfb-120">See also</span></span>

- [<span data-ttu-id="6ecfb-121">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="6ecfb-121">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="6ecfb-122">Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler</span><span class="sxs-lookup"><span data-stu-id="6ecfb-122">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)
- [<span data-ttu-id="6ecfb-123">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="6ecfb-123">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
