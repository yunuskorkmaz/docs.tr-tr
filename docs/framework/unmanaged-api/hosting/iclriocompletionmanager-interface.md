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
ms.openlocfilehash: b63d4269a8d48ee49016a4c51d63bf81bdba8da2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141021"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="ea1c3-102">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea1c3-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="ea1c3-103">Ana bilgisayarın, belirtilen g/ç isteklerinin durumunun ortak dil çalışma zamanına (CLR) bildirmesini sağlayan bir geri çağırma yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="ea1c3-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea1c3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ea1c3-104">Methods</span></span>  
  
|<span data-ttu-id="ea1c3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ea1c3-105">Method</span></span>|<span data-ttu-id="ea1c3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea1c3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea1c3-107">OnComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea1c3-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="ea1c3-108">[Ihostiocompletionmanager:: bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) yöntemine bir çağrı kullanılarak yapılan bir g/ç isteğinin clr 'ye bildirir.</span><span class="sxs-lookup"><span data-stu-id="ea1c3-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea1c3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea1c3-109">Remarks</span></span>  
 <span data-ttu-id="ea1c3-110">Konak, [ıhostiocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) arabirimini kullanarak g/ç tamamlama soyutlama uygular.</span><span class="sxs-lookup"><span data-stu-id="ea1c3-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="ea1c3-111">CLR bu arabirim aracılığıyla g/ç istekleri yapar ve ana bilgisayar `ICLRIoCompletionManager` arabirimini kullanarak bu tür isteklerin çalışma zamanına bildirir.</span><span class="sxs-lookup"><span data-stu-id="ea1c3-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea1c3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea1c3-112">Requirements</span></span>  
 <span data-ttu-id="ea1c3-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea1c3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea1c3-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ea1c3-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea1c3-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ea1c3-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea1c3-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea1c3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea1c3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea1c3-117">See also</span></span>

- [<span data-ttu-id="ea1c3-118">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea1c3-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="ea1c3-119">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea1c3-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="ea1c3-120">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ea1c3-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
