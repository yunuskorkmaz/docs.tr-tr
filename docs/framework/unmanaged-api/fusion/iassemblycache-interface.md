---
title: IAssemblyCache Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache
helpviewer_keywords: IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6244e6c3b0cc88c50cda050a480f5af5b3996b47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="97aa3-102">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97aa3-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="97aa3-103">Kullanmak için Genel Derleme Önbelleği fusion teknolojisiyle temsil eder.</span><span class="sxs-lookup"><span data-stu-id="97aa3-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97aa3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="97aa3-104">Methods</span></span>  
  
|<span data-ttu-id="97aa3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="97aa3-105">Method</span></span>|<span data-ttu-id="97aa3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97aa3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97aa3-107">Createassemblycacheıtem yöntemi</span><span class="sxs-lookup"><span data-stu-id="97aa3-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="97aa3-108">Yeni bir başvuru alır [Iassemblycacheıtem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="97aa3-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="97aa3-109">CreateAssemblyScavenger yöntemi</span><span class="sxs-lookup"><span data-stu-id="97aa3-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="97aa3-110">Fusion teknolojisiyle iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="97aa3-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="97aa3-111">Installassembly yöntemi</span><span class="sxs-lookup"><span data-stu-id="97aa3-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="97aa3-112">Belirtilen derleme genel derleme önbelleğinde yükler.</span><span class="sxs-lookup"><span data-stu-id="97aa3-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="97aa3-113">Queryassemblyınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="97aa3-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="97aa3-114">Belirtilen derleme hakkında istenen verileri alır.</span><span class="sxs-lookup"><span data-stu-id="97aa3-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="97aa3-115">UninstallAssembly yöntemi</span><span class="sxs-lookup"><span data-stu-id="97aa3-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="97aa3-116">Belirtilen derleme Genel Derleme Önbelleği'nden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="97aa3-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97aa3-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97aa3-117">Requirements</span></span>  
 <span data-ttu-id="97aa3-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97aa3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97aa3-119">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="97aa3-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="97aa3-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97aa3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97aa3-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97aa3-121">See Also</span></span>  
 [<span data-ttu-id="97aa3-122">Fusion arabirimleri</span><span class="sxs-lookup"><span data-stu-id="97aa3-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="97aa3-123">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="97aa3-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
