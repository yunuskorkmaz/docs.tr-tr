---
title: ICLRIoCompletionManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRIoCompletionManager
helpviewer_keywords: ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99dc183674abaff33047f070c14794150a8615f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="d981f-102">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d981f-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="d981f-103">Implements belirtilen g/ç durumunu ortak dil çalışma zamanı (CLR) bilgilendirmek için ana izin veren bir geri çağırma yöntemi ister.</span><span class="sxs-lookup"><span data-stu-id="d981f-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d981f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d981f-104">Methods</span></span>  
  
|<span data-ttu-id="d981f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d981f-105">Method</span></span>|<span data-ttu-id="d981f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d981f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d981f-107">OnComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d981f-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="d981f-108">CLR yapılan bir çağrı kullanılarak yapılan bir g/ç isteği durumunu bildirir [Ihostıocompletionmanager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d981f-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d981f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d981f-109">Remarks</span></span>  
 <span data-ttu-id="d981f-110">Ana bilgisayar kullanarak g/ç tamamlama soyutlama uygulayan [Ihostıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d981f-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="d981f-111">CLR g/ç istekleri bu arabirimi aracılığıyla yapar ve kullanarak bu tür istekleri sonucunu çalışma zamanı ana bildirir `ICLRIoCompletionManager` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d981f-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d981f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d981f-112">Requirements</span></span>  
 <span data-ttu-id="d981f-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d981f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d981f-114">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d981f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d981f-115">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d981f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d981f-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d981f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d981f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d981f-117">See Also</span></span>  
 [<span data-ttu-id="d981f-118">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d981f-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="d981f-119">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d981f-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [<span data-ttu-id="d981f-120">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d981f-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
