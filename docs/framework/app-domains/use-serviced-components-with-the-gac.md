---
title: Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4edc675e0348f06114b8162022f1d9420e0cec52
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053058"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="64092-102">Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="64092-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="64092-103">Hizmet verilen bileşenler (yönetilen kod COM+ bileşenleri), genel derleme önbelleğine yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="64092-103">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="64092-104">Bazı senaryolarda, ortak dil çalışma zamanı ve COM+ Hizmetleri, genel derleme önbelleğinde olmayan hizmet verilen bileşenleri işleyebilir; diğer senaryolarda, bunları kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="64092-104">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="64092-105">Aşağıdaki senaryolarda şunlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="64092-105">The following scenarios illustrate this:</span></span>  
  
- <span data-ttu-id="64092-106">COM+ sunucu uygulamasındaki hizmet verilen bileşenler için, Dllhost. exe, hizmet verilen bileşenleri içeren dizin ile aynı dizinde çalıştırılmadığından, bileşenleri içeren derlemenin genel derleme önbelleğinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="64092-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
- <span data-ttu-id="64092-107">Bir COM+ kitaplığı uygulamasındaki hizmet verilen bileşenler için, çalışma zamanı ve COM+ Hizmetleri, geçerli dizinde arama yaparak bileşenleri içeren derleme başvurusunu çözümleyebilir.</span><span class="sxs-lookup"><span data-stu-id="64092-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="64092-108">Bu durumda, derlemenin genel derleme önbelleğinde olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="64092-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
- <span data-ttu-id="64092-109">Bir ASP.NET uygulamasındaki hizmet verilen bileşenler için, durum farklıdır.</span><span class="sxs-lookup"><span data-stu-id="64092-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="64092-110">Hizmet verilen bileşenleri içeren derlemeyi uygulama tabanının bin dizinine yerleştirirseniz ve isteğe bağlı kaydı kullanıyorsanız, ASP.NET, çalışma zamanının gölge özelliklerini kullandığından, derleme indirme önbelleğine gölge olarak kopyalanacaktır.</span><span class="sxs-lookup"><span data-stu-id="64092-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64092-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64092-111">See also</span></span>

- [<span data-ttu-id="64092-112">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="64092-112">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="64092-113">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="64092-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
