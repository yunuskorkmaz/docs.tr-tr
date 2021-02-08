---
description: 'Şu konuda daha fazla bilgi edinin: IHostTask:: Start yöntemi'
title: IHostTask::Start Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 48352a3df49ba2ef3e008ed211da19f54deb82f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784632"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="56fe2-103">IHostTask::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56fe2-103">IHostTask::Start Method</span></span>

<span data-ttu-id="56fe2-104">Konağın geçerli [IHostTask](ihosttask-interface.md) örneği tarafından temsil edilen görevi, askıya alınan görevin, bu kodun yürütülebileceğini canlı bir duruma taşımasını ister.</span><span class="sxs-lookup"><span data-stu-id="56fe2-104">Requests that the host move the task represented by the current [IHostTask](ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fe2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="56fe2-105">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="56fe2-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="56fe2-106">Return Value</span></span>  
  
|<span data-ttu-id="56fe2-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56fe2-107">HRESULT</span></span>|<span data-ttu-id="56fe2-108">Description</span><span class="sxs-lookup"><span data-stu-id="56fe2-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56fe2-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="56fe2-109">S_OK</span></span>|<span data-ttu-id="56fe2-110">Başlatma başarıyla geri döndü.</span><span class="sxs-lookup"><span data-stu-id="56fe2-110">Start returned successfully.</span></span>|  
|<span data-ttu-id="56fe2-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="56fe2-111">E_FAIL</span></span>|<span data-ttu-id="56fe2-112">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="56fe2-112">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="56fe2-113">Bir yöntem E_FAIL döndürdüğünde, ortak dil çalışma zamanı (CLR) artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="56fe2-113">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="56fe2-114">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="56fe2-114">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56fe2-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56fe2-115">Remarks</span></span>  

 <span data-ttu-id="56fe2-116">`Start` her zaman, çok zararlı bir hatanın gerçekleştiği durumlar dışında S_OK bir HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="56fe2-116">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56fe2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56fe2-117">Requirements</span></span>  

 <span data-ttu-id="56fe2-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56fe2-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56fe2-119">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="56fe2-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56fe2-120">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="56fe2-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56fe2-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56fe2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fe2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56fe2-122">See also</span></span>

- [<span data-ttu-id="56fe2-123">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56fe2-123">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="56fe2-124">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56fe2-124">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="56fe2-125">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56fe2-125">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="56fe2-126">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56fe2-126">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
