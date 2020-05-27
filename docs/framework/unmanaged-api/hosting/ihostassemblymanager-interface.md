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
ms.openlocfilehash: 8106dd70f6c4099b2246530622f0845f22a0c53f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805049"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="e75cf-102">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e75cf-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="e75cf-103">Bir konağın ortak dil çalışma zamanı (CLR) veya ana bilgisayar tarafından yüklenmesi gereken derleme kümelerini belirtmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e75cf-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e75cf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e75cf-104">Methods</span></span>  
  
|<span data-ttu-id="e75cf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e75cf-105">Method</span></span>|<span data-ttu-id="e75cf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e75cf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e75cf-107">GetAssemblyStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e75cf-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="e75cf-108">Konak tarafından yüklenen derlemelerin listesini temsil eden bir [IHostAssemblyStore](ihostassemblystore-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e75cf-108">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="e75cf-109">GetNonHostStoreAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e75cf-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="e75cf-110">Konağın CLR 'nin yüklenmesini beklediği derlemelerin listesini temsil eden bir [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) öğesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e75cf-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e75cf-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e75cf-111">Remarks</span></span>  
 <span data-ttu-id="e75cf-112">Konak veya uygulamak için gerekli değildir `IHostAssemblyManager` `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="e75cf-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="e75cf-113">Ana bilgisayar uygulıyorsa `IHostAssemblyManager` , de uygulaması gerekir `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="e75cf-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="e75cf-114">Çalışma zamanı, bir `IHostAssemblyManager` IID_IHostAssemblyManager ile başlatma sonrasında [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) çağırarak bir için sorgular `IID` .</span><span class="sxs-lookup"><span data-stu-id="e75cf-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e75cf-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e75cf-115">Requirements</span></span>  
 <span data-ttu-id="e75cf-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e75cf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e75cf-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e75cf-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e75cf-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e75cf-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e75cf-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e75cf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e75cf-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e75cf-120">See also</span></span>

- [<span data-ttu-id="e75cf-121">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e75cf-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e75cf-122">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e75cf-122">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="e75cf-123">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e75cf-123">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="e75cf-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e75cf-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
