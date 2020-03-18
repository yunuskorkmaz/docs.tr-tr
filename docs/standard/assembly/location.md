---
title: Derleme konumu
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 0b84aba749625f0f86027cd9d09a5e9a2229a3f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733133"
---
# <a name="assembly-location"></a><span data-ttu-id="7c40e-102">Derleme konumu</span><span class="sxs-lookup"><span data-stu-id="7c40e-102">Assembly location</span></span>
<span data-ttu-id="7c40e-103">Bir derlemenin konumu, ortak dil çalışma zamanının başvurulduğunda onu bulup bulamayacağını belirler ve derlemenin diğer derlemelerle paylaşılıp paylaşılamayacağını da belirler.</span><span class="sxs-lookup"><span data-stu-id="7c40e-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="7c40e-104">Bir derlemeyi aşağıdaki konumlara dağıtabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7c40e-104">You can deploy an assembly in the following locations:</span></span>

- <span data-ttu-id="7c40e-105">Uygulamanın dizin veya alt dizinleri.</span><span class="sxs-lookup"><span data-stu-id="7c40e-105">The application's directory or subdirectories.</span></span>

     <span data-ttu-id="7c40e-106">Bu, bir derlemedağıtmak için en yaygın konumdur.</span><span class="sxs-lookup"><span data-stu-id="7c40e-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="7c40e-107">Bir uygulamanın kök dizininin alt dizinleri dil veya kültüre dayalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c40e-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="7c40e-108">Bir derlemekültür özniteliği bilgi varsa, bu kültürün adı ile uygulama dizininin altında bir alt dizini olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c40e-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>

- <span data-ttu-id="7c40e-109">Genel derleme önbelleği.</span><span class="sxs-lookup"><span data-stu-id="7c40e-109">The global assembly cache.</span></span>

     <span data-ttu-id="7c40e-110">Bu, ortak dil çalışma zamanının yüklendiğinde, makine çapında bir kod önbelleğidir.</span><span class="sxs-lookup"><span data-stu-id="7c40e-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="7c40e-111">Çoğu durumda, bir derlemeyi birden çok uygulamayla paylaşmayı planlıyorsanız, derlemeyi genel derleme önbelleğine dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c40e-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>

- <span data-ttu-id="7c40e-112">Bir HTTP sunucusunda.</span><span class="sxs-lookup"><span data-stu-id="7c40e-112">On an HTTP server.</span></span>

     <span data-ttu-id="7c40e-113">BIR HTTP sunucusunda dağıtılan bir derlemenin güçlü bir adı olmalıdır; uygulamanın yapılandırma dosyasının codebase bölümünde derlemeişaret.</span><span class="sxs-lookup"><span data-stu-id="7c40e-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c40e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c40e-114">See also</span></span>

- [<span data-ttu-id="7c40e-115">Derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="7c40e-115">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="7c40e-116">Genel montaj önbelleği</span><span class="sxs-lookup"><span data-stu-id="7c40e-116">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="7c40e-117">Çalışma zamanı derlemeleri nasıl bulur?</span><span class="sxs-lookup"><span data-stu-id="7c40e-117">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
