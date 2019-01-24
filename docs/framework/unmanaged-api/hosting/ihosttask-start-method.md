---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec781a4b51b425225339c08ec8fa194da1972462
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625711"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="838b2-102">IHostTask::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="838b2-102">IHostTask::Start Method</span></span>
<span data-ttu-id="838b2-103">Ana bilgisayar geçerli tarafından temsil edilen görevi taşıma istekler [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) askıya alınmış bir örneğinden Canlı durumuna, hangi kod yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="838b2-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="838b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="838b2-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="838b2-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="838b2-105">Return Value</span></span>  
  
|<span data-ttu-id="838b2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="838b2-106">HRESULT</span></span>|<span data-ttu-id="838b2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="838b2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="838b2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="838b2-108">S_OK</span></span>|<span data-ttu-id="838b2-109">Başlangıç başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="838b2-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="838b2-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="838b2-110">E_FAIL</span></span>|<span data-ttu-id="838b2-111">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="838b2-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="838b2-112">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürüldüğünde, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="838b2-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="838b2-113">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="838b2-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="838b2-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="838b2-114">Remarks</span></span>  
 <span data-ttu-id="838b2-115">`Start` her zaman, S_OK HRESULT değerini dışında bir arıza oluştuğu durumlarda döndürür.</span><span class="sxs-lookup"><span data-stu-id="838b2-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="838b2-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="838b2-116">Requirements</span></span>  
 <span data-ttu-id="838b2-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="838b2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="838b2-118">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="838b2-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="838b2-119">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="838b2-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="838b2-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="838b2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="838b2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="838b2-121">See also</span></span>
- [<span data-ttu-id="838b2-122">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="838b2-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="838b2-123">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="838b2-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="838b2-124">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="838b2-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="838b2-125">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="838b2-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
