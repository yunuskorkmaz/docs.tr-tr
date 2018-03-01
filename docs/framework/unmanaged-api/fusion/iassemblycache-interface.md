---
title: IAssemblyCache Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 21ebc29a6c442625f7a532f7b1e6a47e7dc4cb69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="83692-102">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83692-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="83692-103">Kullanmak için Genel Derleme Önbelleği fusion teknolojisiyle temsil eder.</span><span class="sxs-lookup"><span data-stu-id="83692-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="83692-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="83692-104">Methods</span></span>  
  
|<span data-ttu-id="83692-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="83692-105">Method</span></span>|<span data-ttu-id="83692-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83692-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="83692-107">CreateAssemblyCacheItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83692-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="83692-108">Yeni bir başvuru alır [Iassemblycacheıtem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="83692-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="83692-109">CreateAssemblyScavenger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83692-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="83692-110">Fusion teknolojisiyle iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="83692-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="83692-111">InstallAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83692-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="83692-112">Belirtilen derleme genel derleme önbelleğinde yükler.</span><span class="sxs-lookup"><span data-stu-id="83692-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="83692-113">QueryAssemblyInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83692-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="83692-114">Belirtilen derleme hakkında istenen verileri alır.</span><span class="sxs-lookup"><span data-stu-id="83692-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="83692-115">UninstallAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83692-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="83692-116">Belirtilen derleme Genel Derleme Önbelleği'nden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="83692-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83692-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83692-117">Requirements</span></span>  
 <span data-ttu-id="83692-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83692-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83692-119">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="83692-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="83692-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83692-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83692-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83692-121">See Also</span></span>  
 [<span data-ttu-id="83692-122">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="83692-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="83692-123">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="83692-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
