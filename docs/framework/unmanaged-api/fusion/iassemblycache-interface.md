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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 157cc9f5f520f376c0c055ab49b116bc7961f421
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641076"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="bc814-102">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc814-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="bc814-103">Genel Derleme Önbelleği kullanmak için fusion teknolojisiyle temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bc814-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc814-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bc814-104">Methods</span></span>  
  
|<span data-ttu-id="bc814-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bc814-105">Method</span></span>|<span data-ttu-id="bc814-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc814-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc814-107">CreateAssemblyCacheItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc814-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="bc814-108">Yeni bir başvuru alır [Iassemblycacheıtem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bc814-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="bc814-109">CreateAssemblyScavenger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc814-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="bc814-110">Fusion teknoloji tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="bc814-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="bc814-111">InstallAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc814-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="bc814-112">Belirtilen derlemeyi genel bütünleştirilmiş kod önbelleğine yükler.</span><span class="sxs-lookup"><span data-stu-id="bc814-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="bc814-113">QueryAssemblyInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc814-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="bc814-114">Belirtilen derleme hakkında istenen verileri alır.</span><span class="sxs-lookup"><span data-stu-id="bc814-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="bc814-115">UninstallAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc814-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="bc814-116">Belirtilen derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bc814-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc814-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc814-117">Requirements</span></span>  
 <span data-ttu-id="bc814-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc814-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc814-119">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="bc814-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bc814-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc814-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc814-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc814-121">See also</span></span>
- [<span data-ttu-id="bc814-122">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bc814-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="bc814-123">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="bc814-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
