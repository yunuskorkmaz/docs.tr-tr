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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7864bb81c3b457bf8ec07cd194d24b29a42bd441
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156071"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="1c27a-102">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c27a-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="1c27a-103">Belirtilen g/ç durumunu ortak dil çalışma zamanı (CLR) bildirmek için ana izin veren bir geri çağırma yöntemi uygular ister.</span><span class="sxs-lookup"><span data-stu-id="1c27a-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c27a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1c27a-104">Methods</span></span>  
  
|<span data-ttu-id="1c27a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1c27a-105">Method</span></span>|<span data-ttu-id="1c27a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c27a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c27a-107">OnComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c27a-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="1c27a-108">CLR bir çağrı kullanılarak yapılan bir g/ç isteğinin durumunu bildirir [Ihostıocompletionmanager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1c27a-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c27a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c27a-109">Remarks</span></span>  
 <span data-ttu-id="1c27a-110">Konak kullanarak g/ç tamamlama soyutlama uygulayan [Ihostıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1c27a-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="1c27a-111">CLR bu arabirimi üzerinden g/ç isteği yapar ve konak gibi isteklerinin sonucunu çalışma zamanını kullanarak bildirir `ICLRIoCompletionManager` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1c27a-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c27a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c27a-112">Requirements</span></span>  
 <span data-ttu-id="1c27a-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c27a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c27a-114">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1c27a-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c27a-115">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1c27a-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="1c27a-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="1c27a-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1c27a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c27a-117">See also</span></span>

- [<span data-ttu-id="1c27a-118">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c27a-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="1c27a-119">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c27a-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="1c27a-120">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1c27a-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
