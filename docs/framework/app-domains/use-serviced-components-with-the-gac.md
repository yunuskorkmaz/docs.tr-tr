---
title: Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma
description: .NET 'teki genel derleme önbelleği ile hizmet verilen bileşenleri (yönetilen kod COM+ bileşenleri) kullanın. CLR ve COM+ hizmetlerinin GAC olmayan bileşenleri işleyebileceğini görün.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
ms.openlocfilehash: 314f804dfcaee64ef364cc881ae76651961294d7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254590"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="cf15b-104">Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="cf15b-104">Using Serviced Components with the Global Assembly Cache</span></span>

<span data-ttu-id="cf15b-105">Hizmet verilen bileşenler (yönetilen kod COM+ bileşenleri), genel derleme önbelleğine yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cf15b-105">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="cf15b-106">Bazı senaryolarda, ortak dil çalışma zamanı ve COM+ Hizmetleri, genel derleme önbelleğinde olmayan hizmet verilen bileşenleri işleyebilir; diğer senaryolarda, bunları kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="cf15b-106">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="cf15b-107">Aşağıdaki senaryolarda şunlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="cf15b-107">The following scenarios illustrate this:</span></span>  
  
- <span data-ttu-id="cf15b-108">Bir COM+ sunucu uygulamasındaki hizmet verilen bileşenler için, bileşenleri içeren derlemenin genel derleme önbelleğinde olması gerekir, çünkü Dllhost.exe, hizmet verilen bileşenleri içeren dizin ile aynı dizinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="cf15b-108">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
- <span data-ttu-id="cf15b-109">Bir COM+ kitaplığı uygulamasındaki hizmet verilen bileşenler için, çalışma zamanı ve COM+ Hizmetleri, geçerli dizinde arama yaparak bileşenleri içeren derleme başvurusunu çözümleyebilir.</span><span class="sxs-lookup"><span data-stu-id="cf15b-109">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="cf15b-110">Bu durumda, derlemenin genel derleme önbelleğinde olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cf15b-110">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
- <span data-ttu-id="cf15b-111">Bir ASP.NET uygulamasındaki hizmet verilen bileşenler için, durum farklıdır.</span><span class="sxs-lookup"><span data-stu-id="cf15b-111">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="cf15b-112">Hizmet verilen bileşenleri içeren derlemeyi uygulama tabanının bin dizinine yerleştirirseniz ve isteğe bağlı kaydı kullanıyorsanız, ASP.NET, çalışma zamanının gölge özelliklerini kullandığından, derleme indirme önbelleğine gölge olarak kopyalanacaktır.</span><span class="sxs-lookup"><span data-stu-id="cf15b-112">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf15b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf15b-113">See also</span></span>

- [<span data-ttu-id="cf15b-114">Derlemeler ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="cf15b-114">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="cf15b-115">Gacutil.exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="cf15b-115">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
