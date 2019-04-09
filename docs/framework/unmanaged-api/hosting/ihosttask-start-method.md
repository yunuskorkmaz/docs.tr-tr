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
ms.openlocfilehash: d45c5b09358430535438734b38e5dce5d1bcdd3e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101633"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="f23d3-102">IHostTask::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f23d3-102">IHostTask::Start Method</span></span>
<span data-ttu-id="f23d3-103">Ana bilgisayar geçerli tarafından temsil edilen görevi taşıma istekler [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) askıya alınmış bir örneğinden Canlı durumuna, hangi kod yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="f23d3-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f23d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f23d3-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f23d3-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f23d3-105">Return Value</span></span>  
  
|<span data-ttu-id="f23d3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f23d3-106">HRESULT</span></span>|<span data-ttu-id="f23d3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f23d3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f23d3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f23d3-108">S_OK</span></span>|<span data-ttu-id="f23d3-109">Başlangıç başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f23d3-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="f23d3-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f23d3-110">E_FAIL</span></span>|<span data-ttu-id="f23d3-111">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f23d3-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f23d3-112">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürüldüğünde, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f23d3-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="f23d3-113">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f23d3-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f23d3-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f23d3-114">Remarks</span></span>  
 `Start` <span data-ttu-id="f23d3-115">her zaman, S_OK HRESULT değerini dışında bir arıza oluştuğu durumlarda döndürür.</span><span class="sxs-lookup"><span data-stu-id="f23d3-115">always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f23d3-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f23d3-116">Requirements</span></span>  
 <span data-ttu-id="f23d3-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f23d3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f23d3-118">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f23d3-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f23d3-119">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f23d3-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f23d3-120">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f23d3-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f23d3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f23d3-121">See also</span></span>

- [<span data-ttu-id="f23d3-122">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f23d3-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f23d3-123">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f23d3-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f23d3-124">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f23d3-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f23d3-125">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f23d3-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
