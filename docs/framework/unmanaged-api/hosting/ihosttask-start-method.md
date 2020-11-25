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
ms.openlocfilehash: 4143c3d25dd5262a10b53708a249910cc79f5314
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720444"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="9c741-102">IHostTask::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c741-102">IHostTask::Start Method</span></span>

<span data-ttu-id="9c741-103">Konağın geçerli [IHostTask](ihosttask-interface.md) örneği tarafından temsil edilen görevi, askıya alınan görevin, bu kodun yürütülebileceğini canlı bir duruma taşımasını ister.</span><span class="sxs-lookup"><span data-stu-id="9c741-103">Requests that the host move the task represented by the current [IHostTask](ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c741-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9c741-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9c741-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9c741-105">Return Value</span></span>  
  
|<span data-ttu-id="9c741-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c741-106">HRESULT</span></span>|<span data-ttu-id="9c741-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c741-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c741-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c741-108">S_OK</span></span>|<span data-ttu-id="9c741-109">Başlatma başarıyla geri döndü.</span><span class="sxs-lookup"><span data-stu-id="9c741-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="9c741-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c741-110">E_FAIL</span></span>|<span data-ttu-id="9c741-111">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9c741-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9c741-112">Bir yöntem E_FAIL döndürdüğünde, ortak dil çalışma zamanı (CLR) artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9c741-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="9c741-113">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c741-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c741-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c741-114">Remarks</span></span>  

 <span data-ttu-id="9c741-115">`Start` her zaman, çok zararlı bir hatanın gerçekleştiği durumlar dışında S_OK bir HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c741-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c741-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c741-116">Requirements</span></span>  

 <span data-ttu-id="9c741-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c741-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c741-118">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9c741-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c741-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9c741-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c741-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c741-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c741-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c741-121">See also</span></span>

- [<span data-ttu-id="9c741-122">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c741-122">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9c741-123">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c741-123">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9c741-124">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c741-124">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9c741-125">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c741-125">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
