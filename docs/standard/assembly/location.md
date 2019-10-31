---
title: Derleme konumu
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: d44fb44db35b60f99583c20432c5998573298044
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107213"
---
# <a name="assembly-location"></a><span data-ttu-id="ba710-102">Derleme konumu</span><span class="sxs-lookup"><span data-stu-id="ba710-102">Assembly location</span></span>
<span data-ttu-id="ba710-103">Bir derlemenin konumu, ortak dil çalışma zamanının başvurulması sırasında bulup belirleyemeyeceğini belirler ve derlemenin diğer Derlemelerle paylaşılıp paylaşılamayacağını da tespit edebilir.</span><span class="sxs-lookup"><span data-stu-id="ba710-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="ba710-104">Bir derlemeyi aşağıdaki konumlarda dağıtabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba710-104">You can deploy an assembly in the following locations:</span></span>  
  
- <span data-ttu-id="ba710-105">Uygulamanın dizini veya alt dizinleri.</span><span class="sxs-lookup"><span data-stu-id="ba710-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="ba710-106">Bu, bir derlemeyi dağıtmaya yönelik en yaygın konumdur.</span><span class="sxs-lookup"><span data-stu-id="ba710-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="ba710-107">Bir uygulamanın kök dizininin alt dizinleri dil veya kültür temelinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba710-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="ba710-108">Bir derlemenin kültür özniteliğinde bilgileri varsa, bu kültür adına sahip uygulama dizini altındaki bir alt dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba710-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
- <span data-ttu-id="ba710-109">Genel derleme önbelleği.</span><span class="sxs-lookup"><span data-stu-id="ba710-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="ba710-110">Bu, ortak dil çalışma zamanının yüklendiği her yerde yüklenen makine genelindeki bir kod önbelleğidir.</span><span class="sxs-lookup"><span data-stu-id="ba710-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="ba710-111">Çoğu durumda, birden çok uygulamayla bir derlemeyi paylaşmayı düşünüyorsanız, onu genel derleme önbelleğine dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba710-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
- <span data-ttu-id="ba710-112">Bir HTTP sunucusunda.</span><span class="sxs-lookup"><span data-stu-id="ba710-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="ba710-113">HTTP sunucusunda dağıtılan bir derlemenin tanımlayıcı adı olması gerekir; uygulamanın yapılandırma dosyasının kod temeli bölümünde derleme üzerine gelin.</span><span class="sxs-lookup"><span data-stu-id="ba710-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba710-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba710-114">See also</span></span>

- [<span data-ttu-id="ba710-115">Derlemeler oluştur</span><span class="sxs-lookup"><span data-stu-id="ba710-115">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="ba710-116">Genel derleme önbelleği</span><span class="sxs-lookup"><span data-stu-id="ba710-116">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="ba710-117">Çalışma zamanının derlemeleri nasıl konumlandırır</span><span class="sxs-lookup"><span data-stu-id="ba710-117">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="ba710-118">Bütünleştirilmiş kod içeren program</span><span class="sxs-lookup"><span data-stu-id="ba710-118">Program with assemblies</span></span>](program.md)
