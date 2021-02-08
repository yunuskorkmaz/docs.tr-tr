---
description: 'Şu konuda daha fazla bilgi edinin: ıclriocompletionmanager arabirimi'
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
ms.openlocfilehash: b2d18f9c9900d448f0c6517520c303eb4258f8d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789901"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="6899f-103">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6899f-103">ICLRIoCompletionManager Interface</span></span>

<span data-ttu-id="6899f-104">Ana bilgisayarın, belirtilen g/ç isteklerinin durumunun ortak dil çalışma zamanına (CLR) bildirmesini sağlayan bir geri çağırma yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="6899f-104">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6899f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6899f-105">Methods</span></span>  
  
|<span data-ttu-id="6899f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6899f-106">Method</span></span>|<span data-ttu-id="6899f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6899f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6899f-108">OnComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6899f-108">OnComplete Method</span></span>](iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="6899f-109">[Ihostiocompletionmanager:: bind](ihostiocompletionmanager-bind-method.md) yöntemine bir çağrı kullanılarak yapılan bir g/ç isteğinin clr 'ye bildirir.</span><span class="sxs-lookup"><span data-stu-id="6899f-109">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6899f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6899f-110">Remarks</span></span>  

 <span data-ttu-id="6899f-111">Konak, [ıhostiocompletionmanager](ihostiocompletionmanager-interface.md) arabirimini kullanarak g/ç tamamlama soyutlama uygular.</span><span class="sxs-lookup"><span data-stu-id="6899f-111">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="6899f-112">CLR bu arabirim aracılığıyla g/ç istekleri yapar ve ana bilgisayar, bu tür isteklerin çalışma zamanına arabirimini kullanarak bildirir `ICLRIoCompletionManager` .</span><span class="sxs-lookup"><span data-stu-id="6899f-112">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6899f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6899f-113">Requirements</span></span>  

 <span data-ttu-id="6899f-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6899f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6899f-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6899f-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6899f-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6899f-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6899f-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6899f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6899f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6899f-118">See also</span></span>

- [<span data-ttu-id="6899f-119">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6899f-119">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="6899f-120">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6899f-120">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="6899f-121">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6899f-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
