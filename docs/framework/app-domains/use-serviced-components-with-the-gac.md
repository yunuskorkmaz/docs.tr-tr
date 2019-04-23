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
ms.openlocfilehash: 4bb09f827726f759383598d18fb80657a7e2ff04
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179068"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="05fba-102">Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="05fba-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="05fba-103">Hizmet verilen bileşenlerin (yönetilen kod COM + bileşenleri) genel derleme önbelleğinde koymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="05fba-103">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="05fba-104">Bazı senaryolarda, COM + Hizmetleri ve ortak dil çalışma zamanı genel derleme önbelleğinde olmayan hizmet verilen bileşenleri işleyebilir; Diğer senaryolarda yapamazlar.</span><span class="sxs-lookup"><span data-stu-id="05fba-104">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="05fba-105">Aşağıdaki senaryolar bu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="05fba-105">The following scenarios illustrate this:</span></span>  
  
-   <span data-ttu-id="05fba-106">Bir COM + sunucu uygulamasında hizmet verilen bileşenleri için servis verilen bileşenleri içeren aynı dizinde Dllhost.exe çalışmadığından bileşenlerini içeren derleme genel derleme önbelleğinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="05fba-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
-   <span data-ttu-id="05fba-107">Bir COM + kitaplık uygulamasında hizmet verilen bileşenleri için çalışma zamanı ve COM + Hizmetleri geçerli dizinde arama yaparak bileşenleri içeren derlemenin başvurusunu çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05fba-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="05fba-108">Bu durumda, derleme genel derleme önbelleğinde olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="05fba-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="05fba-109">Bir ASP.NET uygulamasında hizmet verilen bileşenleri için durum farklıdır.</span><span class="sxs-lookup"><span data-stu-id="05fba-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="05fba-110">Uygulama temel bin dizininde servis verilen bileşenleri içeren derlemenin yerleştirin ve isteğe bağlı kayıt kullanıyorsanız, ASP.NET çalışma zamanı gölge yeteneklerini kullanır çünkü derleme indirme önbelleğe gölge kopyalar olacaktır.</span><span class="sxs-lookup"><span data-stu-id="05fba-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05fba-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05fba-111">See also</span></span>

- [<span data-ttu-id="05fba-112">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="05fba-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="05fba-113">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="05fba-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
