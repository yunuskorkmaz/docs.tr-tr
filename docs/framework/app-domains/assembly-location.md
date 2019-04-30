---
title: Derleme Konumu
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c638531bd54f14c7e4b04a093deaec729db404ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675110"
---
# <a name="assembly-location"></a><span data-ttu-id="063b8-102">Derleme Konumu</span><span class="sxs-lookup"><span data-stu-id="063b8-102">Assembly Location</span></span>
<span data-ttu-id="063b8-103">Derlemenin konumunu ortak dil çalışma zamanı başvurulduğunda bulmak, derleme diğer derlemeleri ile paylaşılan olup olmadığını belirlemek olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="063b8-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="063b8-104">Bir derlemeyi aşağıdaki konumlarda dağıtabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="063b8-104">You can deploy an assembly in the following locations:</span></span>  
  
- <span data-ttu-id="063b8-105">Uygulamanın dizin veya alt dizinleri.</span><span class="sxs-lookup"><span data-stu-id="063b8-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="063b8-106">Bu, bir derlemenin dağıtımı için en yaygın konumdur.</span><span class="sxs-lookup"><span data-stu-id="063b8-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="063b8-107">Uygulamaya ait kök dizinin alt dizinlerinin dil veya kültür temel alabilir.</span><span class="sxs-lookup"><span data-stu-id="063b8-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="063b8-108">Bir derlemeyi kültüre özniteliğinde bilgisi yoksa, bu kültürün adı ile uygulama dizininin bir alt dizinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="063b8-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
- <span data-ttu-id="063b8-109">Genel Derleme Önbelleği.</span><span class="sxs-lookup"><span data-stu-id="063b8-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="063b8-110">Ortak dil çalışma zamanı yüklü olduğu her yerde, yüklü olan bir makine düzeyinde kod önbelleği budur.</span><span class="sxs-lookup"><span data-stu-id="063b8-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="063b8-111">Bir derlemeyi birden çok uygulama ile paylaşmak istiyorsanız, çoğu durumda, bu genel bütünleştirilmiş kod önbelleğine dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="063b8-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
- <span data-ttu-id="063b8-112">Bir HTTP sunucusu.</span><span class="sxs-lookup"><span data-stu-id="063b8-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="063b8-113">Bir HTTP sunucusu üzerinde dağıtılan bir derlemeyi tanımlayıcı bir ada sahip olmalıdır; Uygulamanın yapılandırma dosyasına bir kod temelinde bölümündeki derleme gelin.</span><span class="sxs-lookup"><span data-stu-id="063b8-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="063b8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="063b8-114">See also</span></span>

- [<span data-ttu-id="063b8-115">Bütünleştirilmiş Kodlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="063b8-115">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="063b8-116">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="063b8-116">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)
- [<span data-ttu-id="063b8-117">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="063b8-117">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="063b8-118">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="063b8-118">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
