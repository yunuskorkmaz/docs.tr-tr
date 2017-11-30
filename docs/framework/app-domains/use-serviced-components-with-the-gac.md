---
title: "Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma"
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
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45fd02c4f87d33766741e6fd023f9b40b9964d63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="a5123-102">Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="a5123-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="a5123-103">Hizmet verilen bileşenleri (yönetilen kod COM + bileşenleri), genel derleme önbelleğinde moduna geçirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a5123-103">Serviced components (managed code COM+ components) should be put in the global assembly cache.</span></span> <span data-ttu-id="a5123-104">Bazı senaryolarda, genel derleme önbelleğinde olmayan hizmet verilen bileşenler Ortak dil çalışma zamanı ve COM + hizmetlerinin işleyebilir; Diğer senaryolarda yapamazlar.</span><span class="sxs-lookup"><span data-stu-id="a5123-104">In some scenarios, the common language runtime and COM+ Services can handle serviced components that are not in the global assembly cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="a5123-105">Aşağıdaki senaryolar bu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a5123-105">The following scenarios illustrate this:</span></span>  
  
-   <span data-ttu-id="a5123-106">Hizmet verilen bileşenleri içeren aynı dizinde Dllhost.exe çalıştırmadığı bir COM + sunucu uygulamasında hizmet verilen bileşenleri için bileşenlerini içeren derleme genel derleme önbelleğinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a5123-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the global assembly cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
-   <span data-ttu-id="a5123-107">COM + kitaplık uygulamasında hizmet verilen bileşenleri için çalışma zamanı ve COM + hizmetlerinin geçerli dizinde arama yaparak bileşenlerini içeren derleme başvurusunu çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5123-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="a5123-108">Bu durumda, derleme genel derleme önbelleğinde olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a5123-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="a5123-109">Bir ASP.NET uygulamasında hizmet verilen bileşenleri için farklı bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="a5123-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="a5123-110">Hizmet verilen bileşenleri uygulamanın taban bin dizinindeki içeren derlemenin yerleştirin ve isteğe bağlı kayıt kullanırsanız, ASP.NET çalışma zamanı gölge özelliklerinden yararlanır çünkü derleme indirme önbelleğine gölge kopyalar olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a5123-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5123-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5123-111">See Also</span></span>  
 [<span data-ttu-id="a5123-112">Derlemeler ve genel derleme önbelleği ile çalışma</span><span class="sxs-lookup"><span data-stu-id="a5123-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="a5123-113">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="a5123-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
