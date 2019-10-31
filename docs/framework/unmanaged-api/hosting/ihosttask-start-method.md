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
ms.openlocfilehash: fe93a3bab267ccca941974b734c86329ad0f4d03
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121345"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="d93ca-102">IHostTask::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d93ca-102">IHostTask::Start Method</span></span>
<span data-ttu-id="d93ca-103">Konağın geçerli [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği tarafından temsil edilen görevi, askıya alınan görevin, bu kodun yürütülebileceğini canlı bir duruma taşımasını ister.</span><span class="sxs-lookup"><span data-stu-id="d93ca-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d93ca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d93ca-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d93ca-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d93ca-105">Return Value</span></span>  
  
|<span data-ttu-id="d93ca-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d93ca-106">HRESULT</span></span>|<span data-ttu-id="d93ca-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d93ca-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d93ca-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d93ca-108">S_OK</span></span>|<span data-ttu-id="d93ca-109">Başlatma başarıyla geri döndü.</span><span class="sxs-lookup"><span data-stu-id="d93ca-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="d93ca-110">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="d93ca-110">E_FAIL</span></span>|<span data-ttu-id="d93ca-111">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d93ca-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d93ca-112">Bir yöntem E_FAıL döndürdüğünde, ortak dil çalışma zamanı (CLR) artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d93ca-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="d93ca-113">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d93ca-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d93ca-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d93ca-114">Remarks</span></span>  
 <span data-ttu-id="d93ca-115">`Start`, çok zararlı bir hatanın gerçekleştiği durumlar dışında her zaman bir HRESULT değeri S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="d93ca-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d93ca-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d93ca-116">Requirements</span></span>  
 <span data-ttu-id="d93ca-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d93ca-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d93ca-118">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d93ca-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d93ca-119">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d93ca-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d93ca-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d93ca-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d93ca-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d93ca-121">See also</span></span>

- [<span data-ttu-id="d93ca-122">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d93ca-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d93ca-123">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d93ca-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d93ca-124">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d93ca-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d93ca-125">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d93ca-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
