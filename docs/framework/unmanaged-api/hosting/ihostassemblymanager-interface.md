---
title: IHostAssemblyManager Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e300d4645939a131ceb8206999d95056b96a678
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118956"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="68f64-102">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68f64-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="68f64-103">Ortak dil çalışma zamanı (CLR) veya ana bilgisayar tarafından yüklenmesi gereken derlemeler kümesini belirtmek konak izin vermek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="68f64-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68f64-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="68f64-104">Methods</span></span>  
  
|<span data-ttu-id="68f64-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="68f64-105">Method</span></span>|<span data-ttu-id="68f64-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68f64-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68f64-107">GetAssemblyStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68f64-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="68f64-108">Bir arabirim işaretçisi alır bir [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) ana bilgisayar tarafından yüklenen derlemelerin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="68f64-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="68f64-109">GetNonHostStoreAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68f64-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="68f64-110">Bir arabirim işaretçisi alır bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) yüklenecek CLR konak bekliyor derlemelerin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="68f64-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68f64-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68f64-111">Remarks</span></span>  
 <span data-ttu-id="68f64-112">Konak uygulamak için gerekli olmayan `IHostAssemblyManager` veya `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="68f64-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="68f64-113">Konak uygularsanız `IHostAssemblyManager`, ayrıca uygulamalıdır `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="68f64-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="68f64-114">Çalışma zamanı sorgular için bir `IHostAssemblyManager` çağırarak [Ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) ile başlatma sırasında bir `IID` IID_IHostAssemblyManager biri.</span><span class="sxs-lookup"><span data-stu-id="68f64-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68f64-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68f64-115">Requirements</span></span>  
 <span data-ttu-id="68f64-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68f64-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f64-117">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="68f64-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68f64-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="68f64-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68f64-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68f64-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f64-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68f64-120">See also</span></span>

- [<span data-ttu-id="68f64-121">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68f64-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="68f64-122">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68f64-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="68f64-123">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68f64-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="68f64-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="68f64-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
