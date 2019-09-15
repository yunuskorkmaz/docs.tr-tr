---
title: Derleme konumu
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6427f7d005c43ef9e83387e865f71009b683a7c4
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973182"
---
# <a name="assembly-location"></a><span data-ttu-id="5246a-102">Derleme konumu</span><span class="sxs-lookup"><span data-stu-id="5246a-102">Assembly location</span></span>
<span data-ttu-id="5246a-103">Bir derlemenin konumu, ortak dil çalışma zamanının başvurulması sırasında bulup belirleyemeyeceğini belirler ve derlemenin diğer Derlemelerle paylaşılıp paylaşılamayacağını da tespit edebilir.</span><span class="sxs-lookup"><span data-stu-id="5246a-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="5246a-104">Bir derlemeyi aşağıdaki konumlarda dağıtabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5246a-104">You can deploy an assembly in the following locations:</span></span>  
  
- <span data-ttu-id="5246a-105">Uygulamanın dizini veya alt dizinleri.</span><span class="sxs-lookup"><span data-stu-id="5246a-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="5246a-106">Bu, bir derlemeyi dağıtmaya yönelik en yaygın konumdur.</span><span class="sxs-lookup"><span data-stu-id="5246a-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="5246a-107">Bir uygulamanın kök dizininin alt dizinleri dil veya kültür temelinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="5246a-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="5246a-108">Bir derlemenin kültür özniteliğinde bilgileri varsa, bu kültür adına sahip uygulama dizini altındaki bir alt dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5246a-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
- <span data-ttu-id="5246a-109">Genel derleme önbelleği.</span><span class="sxs-lookup"><span data-stu-id="5246a-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="5246a-110">Bu, ortak dil çalışma zamanının yüklendiği her yerde yüklenen makine genelindeki bir kod önbelleğidir.</span><span class="sxs-lookup"><span data-stu-id="5246a-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="5246a-111">Çoğu durumda, birden çok uygulamayla bir derlemeyi paylaşmayı düşünüyorsanız, onu genel derleme önbelleğine dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5246a-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
- <span data-ttu-id="5246a-112">Bir HTTP sunucusunda.</span><span class="sxs-lookup"><span data-stu-id="5246a-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="5246a-113">HTTP sunucusunda dağıtılan bir derlemenin tanımlayıcı adı olması gerekir; uygulamanın yapılandırma dosyasının kod temeli bölümünde derleme üzerine gelin.</span><span class="sxs-lookup"><span data-stu-id="5246a-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5246a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5246a-114">See also</span></span>

- [<span data-ttu-id="5246a-115">Derlemeler oluştur</span><span class="sxs-lookup"><span data-stu-id="5246a-115">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="5246a-116">Genel derleme önbelleği</span><span class="sxs-lookup"><span data-stu-id="5246a-116">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="5246a-117">Çalışma zamanının derlemeleri nasıl konumlandırır</span><span class="sxs-lookup"><span data-stu-id="5246a-117">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="5246a-118">Bütünleştirilmiş kod içeren program</span><span class="sxs-lookup"><span data-stu-id="5246a-118">Program with assemblies</span></span>](program.md)
