---
description: 'Şu konuda daha fazla bilgi edinin: IHostAssemblyManager arabirimi'
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
ms.openlocfilehash: 649771f79e65039adfa8c0ade9f167b1679bb917
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709002"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="92091-103">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92091-103">IHostAssemblyManager Interface</span></span>

<span data-ttu-id="92091-104">Bir konağın ortak dil çalışma zamanı (CLR) veya ana bilgisayar tarafından yüklenmesi gereken derleme kümelerini belirtmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="92091-104">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92091-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="92091-105">Methods</span></span>  
  
|<span data-ttu-id="92091-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="92091-106">Method</span></span>|<span data-ttu-id="92091-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92091-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92091-108">GetAssemblyStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92091-108">GetAssemblyStore Method</span></span>](ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="92091-109">Konak tarafından yüklenen derlemelerin listesini temsil eden bir [IHostAssemblyStore](ihostassemblystore-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="92091-109">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="92091-110">GetNonHostStoreAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92091-110">GetNonHostStoreAssemblies Method</span></span>](ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="92091-111">Konağın CLR 'nin yüklenmesini beklediği derlemelerin listesini temsil eden bir [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) öğesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="92091-111">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92091-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92091-112">Remarks</span></span>  

 <span data-ttu-id="92091-113">Konak veya uygulamak için gerekli değildir `IHostAssemblyManager` `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="92091-113">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="92091-114">Ana bilgisayar uygulıyorsa `IHostAssemblyManager` , de uygulaması gerekir `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="92091-114">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="92091-115">Çalışma zamanı, bir `IHostAssemblyManager` IID_IHostAssemblyManager ile başlatma sonrasında [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) çağırarak bir için sorgular `IID` .</span><span class="sxs-lookup"><span data-stu-id="92091-115">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92091-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92091-116">Requirements</span></span>  

 <span data-ttu-id="92091-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92091-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92091-118">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="92091-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92091-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="92091-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92091-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92091-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92091-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92091-121">See also</span></span>

- [<span data-ttu-id="92091-122">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92091-122">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="92091-123">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92091-123">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="92091-124">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92091-124">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="92091-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="92091-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
