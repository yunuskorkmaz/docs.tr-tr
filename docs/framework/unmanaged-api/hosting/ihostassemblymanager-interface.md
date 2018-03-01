---
title: IHostAssemblyManager Arabirimi
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
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 351824c1b915183a8e157f5bb2e01a414027a178
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="53623-102">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53623-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="53623-103">Ortak dil çalışma zamanı (CLR) veya ana bilgisayar tarafından yüklenmesi gereken derlemeler kümesini belirtmek bir konak izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="53623-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53623-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="53623-104">Methods</span></span>  
  
|<span data-ttu-id="53623-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="53623-105">Method</span></span>|<span data-ttu-id="53623-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53623-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="53623-107">GetAssemblyStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53623-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="53623-108">Bir arabirim işaretçisi alır bir [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) ana bilgisayar tarafından yüklenen derleme listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="53623-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="53623-109">GetNonHostStoreAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53623-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="53623-110">Bir arabirim işaretçisi alır bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) yüklemek için CLR konak bekliyor derleme listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="53623-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53623-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53623-111">Remarks</span></span>  
 <span data-ttu-id="53623-112">Ana bilgisayar uygulamak için gerekli olmayan `IHostAssemblyManager` veya `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="53623-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="53623-113">Ana bilgisayar uygularsanız `IHostAssemblyManager`, ayrıca uygulamalıdır `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="53623-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="53623-114">Çalışma zamanı sorgular için bir `IHostAssemblyManager` çağırarak [Ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) ile başlatma sırasında bir `IID` IID_IHostAssemblyManager biri.</span><span class="sxs-lookup"><span data-stu-id="53623-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53623-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53623-115">Requirements</span></span>  
 <span data-ttu-id="53623-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53623-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53623-117">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="53623-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53623-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="53623-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53623-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53623-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53623-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="53623-120">See Also</span></span>  
 [<span data-ttu-id="53623-121">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53623-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="53623-122">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53623-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="53623-123">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53623-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="53623-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="53623-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
