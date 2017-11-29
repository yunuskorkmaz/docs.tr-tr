---
title: Derleme Konumu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e069c1636004896bfb193fd70a352195ba045865
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-location"></a><span data-ttu-id="5bdb7-102">Derleme Konumu</span><span class="sxs-lookup"><span data-stu-id="5bdb7-102">Assembly Location</span></span>
<span data-ttu-id="5bdb7-103">Derlemenin konumunu ortak dil çalışma zamanı, başvurulan sırasında bulabilir ve da derlemeyi diğer Derlemelerle paylaşılabilir olup olmadığını belirlemeniz olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="5bdb7-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="5bdb7-104">Bir derlemeyi aşağıdaki konumlarda dağıtabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5bdb7-104">You can deploy an assembly in the following locations:</span></span>  
  
-   <span data-ttu-id="5bdb7-105">Uygulamanın dizin veya dizin.</span><span class="sxs-lookup"><span data-stu-id="5bdb7-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="5bdb7-106">Bu, bir derlemeyi dağıtmak için en yaygın konumdur.</span><span class="sxs-lookup"><span data-stu-id="5bdb7-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="5bdb7-107">Bir uygulamanın kök dizininin alt dizinleri dil veya kültür dayalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5bdb7-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="5bdb7-108">Derleme kültür özniteliğinde bilgi varsa, bu kültürün adıyla uygulama dizininin altında bir alt dizinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5bdb7-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
-   <span data-ttu-id="5bdb7-109">Genel Derleme Önbelleği.</span><span class="sxs-lookup"><span data-stu-id="5bdb7-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="5bdb7-110">Bu ortak dil çalışma zamanı yüklü olduğunda, yüklü olduğu bir makineye kod önbelleğidir.</span><span class="sxs-lookup"><span data-stu-id="5bdb7-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="5bdb7-111">Birden çok uygulama ile bir derlemeyi paylaşmak istiyorsanız, çoğu durumda, bu genel derleme önbelleğine dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5bdb7-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="5bdb7-112">Bir HTTP sunucusunda.</span><span class="sxs-lookup"><span data-stu-id="5bdb7-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="5bdb7-113">Bir HTTP sunucusu üzerinde dağıtılan bir derleme tanımlayıcı adı olmalıdır; Uygulamanın yapılandırma dosyasına codebase bölümünü derlemede üzerine gelin.</span><span class="sxs-lookup"><span data-stu-id="5bdb7-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bdb7-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5bdb7-114">See Also</span></span>  
 [<span data-ttu-id="5bdb7-115">Derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="5bdb7-115">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="5bdb7-116">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="5bdb7-116">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="5bdb7-117">Çalışma zamanı derlemeleri nasıl bulur</span><span class="sxs-lookup"><span data-stu-id="5bdb7-117">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="5bdb7-118">Derlemelerle programlama</span><span class="sxs-lookup"><span data-stu-id="5bdb7-118">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
