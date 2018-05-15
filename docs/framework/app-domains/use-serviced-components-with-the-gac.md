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
ms.openlocfilehash: 703e71661c7a679b85e60726f53b275fce1a4d6a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="f6072-102">Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f6072-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="f6072-103">Hizmet verilen bileşenleri (yönetilen kod COM + bileşenleri), Genel Derleme Önbelleği'nde moduna geçirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f6072-103">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="f6072-104">Bazı senaryolarda, Genel Derleme Önbelleği'nde olmayan hizmet verilen bileşenler Ortak dil çalışma zamanı ve COM + hizmetlerinin işleyebilir; Diğer senaryolarda yapamazlar.</span><span class="sxs-lookup"><span data-stu-id="f6072-104">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="f6072-105">Aşağıdaki senaryolar bu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f6072-105">The following scenarios illustrate this:</span></span>  
  
-   <span data-ttu-id="f6072-106">Hizmet verilen bileşenleri içeren aynı dizinde Dllhost.exe çalıştırmadığı bir COM + sunucu uygulamasında hizmet verilen bileşenleri için bileşenlerini içeren derleme Genel Derleme Önbelleği'olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6072-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
-   <span data-ttu-id="f6072-107">COM + kitaplık uygulamasında hizmet verilen bileşenleri için çalışma zamanı ve COM + hizmetlerinin geçerli dizinde arama yaparak bileşenlerini içeren derleme başvurusunu çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6072-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="f6072-108">Bu durumda, derleme genel derleme önbelleğinde olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f6072-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="f6072-109">Bir ASP.NET uygulamasında hizmet verilen bileşenleri için farklı bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="f6072-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="f6072-110">Hizmet verilen bileşenleri uygulamanın taban bin dizinindeki içeren derlemenin yerleştirin ve isteğe bağlı kayıt kullanırsanız, ASP.NET çalışma zamanı gölge özelliklerinden yararlanır çünkü derleme indirme önbelleğine gölge kopyalar olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f6072-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6072-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6072-111">See Also</span></span>  
 [<span data-ttu-id="f6072-112">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="f6072-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="f6072-113">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="f6072-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
