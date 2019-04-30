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
ms.openlocfilehash: 9fc5f3a3d5bc5699a596bcc648a7153190c130f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697686"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="09222-102">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09222-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="09222-103">Genel Derleme Önbelleği kullanmak için fusion teknolojisiyle temsil eder.</span><span class="sxs-lookup"><span data-stu-id="09222-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09222-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="09222-104">Methods</span></span>  
  
|<span data-ttu-id="09222-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="09222-105">Method</span></span>|<span data-ttu-id="09222-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09222-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09222-107">CreateAssemblyCacheItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09222-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="09222-108">Yeni bir başvuru alır [Iassemblycacheıtem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="09222-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="09222-109">CreateAssemblyScavenger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09222-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="09222-110">Fusion teknoloji tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="09222-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="09222-111">InstallAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09222-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="09222-112">Belirtilen derlemeyi genel bütünleştirilmiş kod önbelleğine yükler.</span><span class="sxs-lookup"><span data-stu-id="09222-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="09222-113">QueryAssemblyInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09222-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="09222-114">Belirtilen derleme hakkında istenen verileri alır.</span><span class="sxs-lookup"><span data-stu-id="09222-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="09222-115">UninstallAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09222-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="09222-116">Belirtilen derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="09222-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09222-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09222-117">Requirements</span></span>  
 <span data-ttu-id="09222-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09222-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09222-119">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="09222-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="09222-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09222-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09222-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09222-121">See also</span></span>

- [<span data-ttu-id="09222-122">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="09222-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="09222-123">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="09222-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
