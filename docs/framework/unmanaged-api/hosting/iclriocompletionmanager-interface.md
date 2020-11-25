---
title: ICLRIoCompletionManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: e23675351e1fd0de510243c9ee8b3a6dd6f29cec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714126"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="35d86-102">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35d86-102">ICLRIoCompletionManager Interface</span></span>

<span data-ttu-id="35d86-103">Ana bilgisayarın, belirtilen g/ç isteklerinin durumunun ortak dil çalışma zamanına (CLR) bildirmesini sağlayan bir geri çağırma yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="35d86-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35d86-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="35d86-104">Methods</span></span>  
  
|<span data-ttu-id="35d86-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="35d86-105">Method</span></span>|<span data-ttu-id="35d86-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35d86-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="35d86-107">OnComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35d86-107">OnComplete Method</span></span>](iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="35d86-108">[Ihostiocompletionmanager:: bind](ihostiocompletionmanager-bind-method.md) yöntemine bir çağrı kullanılarak yapılan bir g/ç isteğinin clr 'ye bildirir.</span><span class="sxs-lookup"><span data-stu-id="35d86-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35d86-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35d86-109">Remarks</span></span>  

 <span data-ttu-id="35d86-110">Konak, [ıhostiocompletionmanager](ihostiocompletionmanager-interface.md) arabirimini kullanarak g/ç tamamlama soyutlama uygular.</span><span class="sxs-lookup"><span data-stu-id="35d86-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="35d86-111">CLR bu arabirim aracılığıyla g/ç istekleri yapar ve ana bilgisayar, bu tür isteklerin çalışma zamanına arabirimini kullanarak bildirir `ICLRIoCompletionManager` .</span><span class="sxs-lookup"><span data-stu-id="35d86-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35d86-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35d86-112">Requirements</span></span>  

 <span data-ttu-id="35d86-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35d86-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35d86-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="35d86-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35d86-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="35d86-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35d86-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35d86-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35d86-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35d86-117">See also</span></span>

- [<span data-ttu-id="35d86-118">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35d86-118">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="35d86-119">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35d86-119">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="35d86-120">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="35d86-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
