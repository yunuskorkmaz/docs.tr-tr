---
title: IHostAssemblyManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager
helpviewer_keywords: IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b3761063201a48303884fdecddddf02558cd4e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="4c816-102">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c816-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="4c816-103">Ortak dil çalışma zamanı (CLR) veya ana bilgisayar tarafından yüklenmesi gereken derlemeler kümesini belirtmek bir konak izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c816-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c816-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4c816-104">Methods</span></span>  
  
|<span data-ttu-id="4c816-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4c816-105">Method</span></span>|<span data-ttu-id="4c816-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c816-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c816-107">GetAssemblyStore yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c816-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="4c816-108">Bir arabirim işaretçisi alır bir [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) ana bilgisayar tarafından yüklenen derleme listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c816-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="4c816-109">GetNonHostStoreAssemblies yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c816-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="4c816-110">Bir arabirim işaretçisi alır bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) yüklemek için CLR konak bekliyor derleme listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c816-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c816-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c816-111">Remarks</span></span>  
 <span data-ttu-id="4c816-112">Ana bilgisayar uygulamak için gerekli olmayan `IHostAssemblyManager` veya `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="4c816-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="4c816-113">Ana bilgisayar uygularsanız `IHostAssemblyManager`, ayrıca uygulamalıdır `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="4c816-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="4c816-114">Çalışma zamanı sorgular için bir `IHostAssemblyManager` çağırarak [Ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) ile başlatma sırasında bir `IID` IID_IHostAssemblyManager biri.</span><span class="sxs-lookup"><span data-stu-id="4c816-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c816-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c816-115">Requirements</span></span>  
 <span data-ttu-id="4c816-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c816-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c816-117">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c816-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c816-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4c816-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c816-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c816-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c816-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c816-120">See Also</span></span>  
 [<span data-ttu-id="4c816-121">Iclrassemblyreferencelist arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c816-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="4c816-122">Ihostassemblystore arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c816-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="4c816-123">Ihostcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c816-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="4c816-124">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4c816-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
