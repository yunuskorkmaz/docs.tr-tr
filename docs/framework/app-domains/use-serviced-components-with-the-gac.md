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
ms.workload: dotnet
ms.openlocfilehash: fb9bd85797dd129f6f34992c58c9772668ce2cb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="5dac4-102">Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="5dac4-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="5dac4-103">Hizmet verilen bileşenleri (yönetilen kod COM + bileşenleri), Genel Derleme Önbelleği'nde moduna geçirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5dac4-103">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="5dac4-104">Bazı senaryolarda, Genel Derleme Önbelleği'nde olmayan hizmet verilen bileşenler Ortak dil çalışma zamanı ve COM + hizmetlerinin işleyebilir; Diğer senaryolarda yapamazlar.</span><span class="sxs-lookup"><span data-stu-id="5dac4-104">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="5dac4-105">Aşağıdaki senaryolar bu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5dac4-105">The following scenarios illustrate this:</span></span>  
  
-   <span data-ttu-id="5dac4-106">Hizmet verilen bileşenleri içeren aynı dizinde Dllhost.exe çalıştırmadığı bir COM + sunucu uygulamasında hizmet verilen bileşenleri için bileşenlerini içeren derleme Genel Derleme Önbelleği'olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5dac4-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
-   <span data-ttu-id="5dac4-107">COM + kitaplık uygulamasında hizmet verilen bileşenleri için çalışma zamanı ve COM + hizmetlerinin geçerli dizinde arama yaparak bileşenlerini içeren derleme başvurusunu çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5dac4-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="5dac4-108">Bu durumda, derleme genel derleme önbelleğinde olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5dac4-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="5dac4-109">Bir ASP.NET uygulamasında hizmet verilen bileşenleri için farklı bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="5dac4-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="5dac4-110">Hizmet verilen bileşenleri uygulamanın taban bin dizinindeki içeren derlemenin yerleştirin ve isteğe bağlı kayıt kullanırsanız, ASP.NET çalışma zamanı gölge özelliklerinden yararlanır çünkü derleme indirme önbelleğine gölge kopyalar olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5dac4-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dac4-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5dac4-111">See Also</span></span>  
 [<span data-ttu-id="5dac4-112">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="5dac4-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="5dac4-113">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="5dac4-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
