---
title: Derleme konumu
description: .NET derlemesinin konumu, CLR 'nin onu nasıl bulduğunu ve diğer Derlemelerle paylaşılıp paylaşılamayacağını belirler.
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 1fa1c486c0cddce4ddcfae7f2df27e2e85c88e66
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687599"
---
# <a name="assembly-location"></a><span data-ttu-id="add41-103">Derleme konumu</span><span class="sxs-lookup"><span data-stu-id="add41-103">Assembly location</span></span>

<span data-ttu-id="add41-104">Bir derlemenin konumu, ortak dil çalışma zamanının başvurulması sırasında bulup belirleyemeyeceğini belirler ve derlemenin diğer Derlemelerle paylaşılıp paylaşılamayacağını da tespit edebilir.</span><span class="sxs-lookup"><span data-stu-id="add41-104">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="add41-105">Bir derlemeyi aşağıdaki konumlarda dağıtabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="add41-105">You can deploy an assembly in the following locations:</span></span>

- <span data-ttu-id="add41-106">Uygulamanın dizini veya alt dizinleri.</span><span class="sxs-lookup"><span data-stu-id="add41-106">The application's directory or subdirectories.</span></span>

     <span data-ttu-id="add41-107">Bu, bir derlemeyi dağıtmaya yönelik en yaygın konumdur.</span><span class="sxs-lookup"><span data-stu-id="add41-107">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="add41-108">Bir uygulamanın kök dizininin alt dizinleri dil veya kültür temelinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="add41-108">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="add41-109">Bir derlemenin kültür özniteliğinde bilgileri varsa, bu kültür adına sahip uygulama dizini altındaki bir alt dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="add41-109">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>

- <span data-ttu-id="add41-110">Genel derleme önbelleği.</span><span class="sxs-lookup"><span data-stu-id="add41-110">The global assembly cache.</span></span>

     <span data-ttu-id="add41-111">Bu, ortak dil çalışma zamanının yüklendiği her yerde yüklenen makine genelindeki bir kod önbelleğidir.</span><span class="sxs-lookup"><span data-stu-id="add41-111">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="add41-112">Çoğu durumda, birden çok uygulamayla bir derlemeyi paylaşmayı düşünüyorsanız, onu genel derleme önbelleğine dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="add41-112">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>

- <span data-ttu-id="add41-113">Bir HTTP sunucusunda.</span><span class="sxs-lookup"><span data-stu-id="add41-113">On an HTTP server.</span></span>

     <span data-ttu-id="add41-114">HTTP sunucusunda dağıtılan bir derlemenin tanımlayıcı adı olması gerekir; uygulamanın yapılandırma dosyasının kod temeli bölümünde derleme üzerine gelin.</span><span class="sxs-lookup"><span data-stu-id="add41-114">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="add41-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="add41-115">See also</span></span>

- [<span data-ttu-id="add41-116">Derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="add41-116">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="add41-117">Genel derleme önbelleği</span><span class="sxs-lookup"><span data-stu-id="add41-117">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="add41-118">Çalışma zamanının derlemeleri nasıl konumlandırır</span><span class="sxs-lookup"><span data-stu-id="add41-118">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
