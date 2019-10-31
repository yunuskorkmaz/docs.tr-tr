---
title: IAssemblyCache Arabirimi
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
ms.openlocfilehash: 5ed0075da1429c70900750f3f28e8ce36a41fb28
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134535"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="95a09-102">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95a09-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="95a09-103">Fusion teknolojisinin kullanması için genel derleme önbelleğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="95a09-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95a09-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="95a09-104">Methods</span></span>  
  
|<span data-ttu-id="95a09-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="95a09-105">Method</span></span>|<span data-ttu-id="95a09-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95a09-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95a09-107">CreateAssemblyCacheItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95a09-107">CreateAssemblyCacheItem Method</span></span>](iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="95a09-108">Yeni bir [IAssemblyCacheItem](iassemblycacheitem-interface.md)öğesine bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="95a09-108">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="95a09-109">CreateAssemblyScavenger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95a09-109">CreateAssemblyScavenger Method</span></span>](iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="95a09-110">Fusion teknolojisinin iç kullanımı için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="95a09-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="95a09-111">InstallAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95a09-111">InstallAssembly Method</span></span>](iassemblycache-installassembly-method.md)|<span data-ttu-id="95a09-112">Belirtilen derlemeyi genel derleme önbelleğine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="95a09-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="95a09-113">QueryAssemblyInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95a09-113">QueryAssemblyInfo Method</span></span>](iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="95a09-114">Belirtilen derleme hakkında istenen verileri alır.</span><span class="sxs-lookup"><span data-stu-id="95a09-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="95a09-115">UninstallAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95a09-115">UninstallAssembly Method</span></span>](iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="95a09-116">Belirtilen derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="95a09-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95a09-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95a09-117">Requirements</span></span>  
 <span data-ttu-id="95a09-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95a09-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95a09-119">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="95a09-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="95a09-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95a09-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a09-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95a09-121">See also</span></span>

- [<span data-ttu-id="95a09-122">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="95a09-122">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="95a09-123">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="95a09-123">Global Assembly Cache</span></span>](../../app-domains/gac.md)
