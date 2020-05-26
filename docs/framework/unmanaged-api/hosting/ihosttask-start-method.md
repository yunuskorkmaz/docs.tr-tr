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
ms.openlocfilehash: a4e8211f091b2a3a4f24d8350f6d7dbe7d7920af
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842398"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="a4f06-102">IHostTask::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4f06-102">IHostTask::Start Method</span></span>
<span data-ttu-id="a4f06-103">Konağın geçerli [IHostTask](ihosttask-interface.md) örneği tarafından temsil edilen görevi, askıya alınan görevin, bu kodun yürütülebileceğini canlı bir duruma taşımasını ister.</span><span class="sxs-lookup"><span data-stu-id="a4f06-103">Requests that the host move the task represented by the current [IHostTask](ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4f06-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4f06-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a4f06-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a4f06-105">Return Value</span></span>  
  
|<span data-ttu-id="a4f06-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a4f06-106">HRESULT</span></span>|<span data-ttu-id="a4f06-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4f06-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4f06-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4f06-108">S_OK</span></span>|<span data-ttu-id="a4f06-109">Başlatma başarıyla geri döndü.</span><span class="sxs-lookup"><span data-stu-id="a4f06-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="a4f06-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a4f06-110">E_FAIL</span></span>|<span data-ttu-id="a4f06-111">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a4f06-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a4f06-112">Bir yöntem E_FAIL döndürdüğünde, ortak dil çalışma zamanı (CLR) artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a4f06-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="a4f06-113">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4f06-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4f06-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4f06-114">Remarks</span></span>  
 <span data-ttu-id="a4f06-115">`Start`her zaman, çok zararlı bir hatanın gerçekleştiği durumlar dışında S_OK bir HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4f06-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4f06-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4f06-116">Requirements</span></span>  
 <span data-ttu-id="a4f06-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4f06-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4f06-118">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a4f06-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4f06-119">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a4f06-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4f06-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4f06-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4f06-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4f06-121">See also</span></span>

- [<span data-ttu-id="a4f06-122">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4f06-122">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a4f06-123">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4f06-123">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a4f06-124">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4f06-124">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a4f06-125">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4f06-125">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
