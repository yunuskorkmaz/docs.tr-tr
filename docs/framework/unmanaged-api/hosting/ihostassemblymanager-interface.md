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
ms.openlocfilehash: d9feeaf5f85d6f84a13e74a893b82c97fdaf023c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124516"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="50161-102">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50161-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="50161-103">Bir konağın ortak dil çalışma zamanı (CLR) veya ana bilgisayar tarafından yüklenmesi gereken derleme kümelerini belirtmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="50161-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50161-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="50161-104">Methods</span></span>  
  
|<span data-ttu-id="50161-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="50161-105">Method</span></span>|<span data-ttu-id="50161-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50161-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50161-107">GetAssemblyStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50161-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="50161-108">Konak tarafından yüklenen derlemelerin listesini temsil eden bir [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="50161-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="50161-109">GetNonHostStoreAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50161-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="50161-110">Konağın CLR 'nin yüklenmesini beklediği derlemelerin listesini temsil eden bir [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) öğesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="50161-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50161-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50161-111">Remarks</span></span>  
 <span data-ttu-id="50161-112">Konağın `IHostAssemblyManager` veya `IHostAssemblyStore`uygulaması için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="50161-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="50161-113">Ana bilgisayar `IHostAssemblyManager`uygulıyorsa, `IHostAssemblyStore`de uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="50161-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="50161-114">Çalışma zamanı, IID_IHostAssemblyManager 'in bir `IID` başlatma sonrasında [IHostControl:: GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) çağırarak bir `IHostAssemblyManager` için sorgular.</span><span class="sxs-lookup"><span data-stu-id="50161-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50161-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50161-115">Requirements</span></span>  
 <span data-ttu-id="50161-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50161-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50161-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="50161-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50161-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="50161-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50161-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50161-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50161-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50161-120">See also</span></span>

- [<span data-ttu-id="50161-121">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50161-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="50161-122">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50161-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="50161-123">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50161-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="50161-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="50161-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
