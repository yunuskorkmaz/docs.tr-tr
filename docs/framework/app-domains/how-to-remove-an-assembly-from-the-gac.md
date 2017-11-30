---
title: "Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğinden Kaldırma"
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
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a17478c350d789d320e97d6b50d6f5f9daaf6db3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="b1795-102">Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğinden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="b1795-102">How to: Remove an Assembly from the Global Assembly Cache</span></span>
<span data-ttu-id="b1795-103">Bir derlemeyi genel derleme önbelleğinden (GAC) kaldırmak için iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="b1795-103">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>  
  
-   <span data-ttu-id="b1795-104">Kullanarak [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b1795-104">By using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="b1795-105">Geliştirme ve sınama sırasında GAC'ye yerleştirdiğiniz derlemeleri kaldırmak için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="b1795-105">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>  
  
-   <span data-ttu-id="b1795-106">Kullanarak [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span><span class="sxs-lookup"><span data-stu-id="b1795-106">By using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span> <span data-ttu-id="b1795-107">Derlemeleri yükleme paketleri sınarken ve üretim sistemleri için kaldırmak için bu seçeneği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1795-107">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>  
  
### <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="b1795-108">Gacutil.exe ile bir derlemeyi kaldırma</span><span class="sxs-lookup"><span data-stu-id="b1795-108">Removing an assembly with Gacutil.exe</span></span>  
  
1.  <span data-ttu-id="b1795-109">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="b1795-109">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="b1795-110">**Gacutil – u** \< *derleme adı*></span><span class="sxs-lookup"><span data-stu-id="b1795-110">**gacutil –u** \<*assembly name*></span></span>  
  
     <span data-ttu-id="b1795-111">Bu komutta *derleme adı* genel derleme önbelleğinden kaldırılacak derleme adıdır.</span><span class="sxs-lookup"><span data-stu-id="b1795-111">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="b1795-112">Gacutil.exe, üretim sistemleri derlemelerini derleme hala bazı uygulama tarafından gerekebilir olasılığı nedeniyle kaldırmak için kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="b1795-112">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="b1795-113">Bunun yerine, her derlemeyi GAC'ye yükler için bir başvuru sayımı tutar Windows Installer kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1795-113">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>  
  
 <span data-ttu-id="b1795-114">Aşağıdaki örnek adlı bir derleme kaldırır `hello.dll` genel derleme önbelleğinden.</span><span class="sxs-lookup"><span data-stu-id="b1795-114">The following example removes an assembly named `hello.dll` from the global assembly cache.</span></span>  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="b1795-115">Windows Installer ile bir derlemeyi kaldırma</span><span class="sxs-lookup"><span data-stu-id="b1795-115">Removing an assembly with Windows Installer</span></span>  
  
1.  <span data-ttu-id="b1795-116">Gelen **programlar ve Özellikler** uygulamada **Denetim Masası**, kaldırmak istediğiniz uygulamayı seçin.</span><span class="sxs-lookup"><span data-stu-id="b1795-116">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="b1795-117">Yükleme paketi GAC'ye derlemeleri yerleştirdiyseniz, başka bir uygulama tarafından kullanılmaz, Windows Installer bunları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b1795-117">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1795-118">Windows Installer GAC'de kurulu derlemeler için bir başvuru sayımı tutar.</span><span class="sxs-lookup"><span data-stu-id="b1795-118">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="b1795-119">Yalnızca kendi başvuru sayısı, Windows Installer paketiyle yüklenen herhangi bir uygulama tarafından kullanılıp kullanılmadığını gösteren sıfır ulaştığında bir derlemeyi GAC kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b1795-119">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1795-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1795-120">See Also</span></span>  
 [<span data-ttu-id="b1795-121">Derlemeler ve genel derleme önbelleği ile çalışma</span><span class="sxs-lookup"><span data-stu-id="b1795-121">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="b1795-122">Nasıl yapılır: bir derlemeyi genel derleme önbelleğine yükleme</span><span class="sxs-lookup"><span data-stu-id="b1795-122">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="b1795-123">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="b1795-123">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
