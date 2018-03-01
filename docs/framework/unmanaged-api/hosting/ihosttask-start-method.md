---
title: "IHostTask::Start Yöntemi"
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
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: db43ec56fac86b0040aa4f701940abf0d1c0df07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="2791e-102">IHostTask::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2791e-102">IHostTask::Start Method</span></span>
<span data-ttu-id="2791e-103">Taşıma geçerli tarafından temsil edilen görevi konak istekleri [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) askıya alınmış bir örnekten, kod yürütülebilir canlı bir duruma.</span><span class="sxs-lookup"><span data-stu-id="2791e-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2791e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2791e-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2791e-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2791e-105">Return Value</span></span>  
  
|<span data-ttu-id="2791e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2791e-106">HRESULT</span></span>|<span data-ttu-id="2791e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2791e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2791e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2791e-108">S_OK</span></span>|<span data-ttu-id="2791e-109">Başlangıç başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2791e-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="2791e-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2791e-110">E_FAIL</span></span>|<span data-ttu-id="2791e-111">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2791e-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2791e-112">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndüğünde, işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2791e-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="2791e-113">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2791e-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2791e-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2791e-114">Remarks</span></span>  
 <span data-ttu-id="2791e-115">`Start`her zaman bir HRESULT değerini S_OK, dışında yıkıcı bir hata oluştuğu durumlarda döndürür.</span><span class="sxs-lookup"><span data-stu-id="2791e-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2791e-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2791e-116">Requirements</span></span>  
 <span data-ttu-id="2791e-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2791e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2791e-118">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2791e-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2791e-119">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2791e-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2791e-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2791e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2791e-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2791e-121">See Also</span></span>  
 [<span data-ttu-id="2791e-122">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2791e-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="2791e-123">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2791e-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="2791e-124">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2791e-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="2791e-125">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2791e-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
