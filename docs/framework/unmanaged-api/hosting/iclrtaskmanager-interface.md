---
title: ICLRTaskManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19ef7cb78791496de76e5741f8254ee88563c776
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134667"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="92810-102">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92810-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="92810-103">Ortak dil çalışma zamanı (CLR) açıkça istemek üzere konağın izin yöntemleri yeni bir görev oluşturma, şu anda yürütülmekte olan görevi Al ve coğrafi dil ve kültür için bir görev kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="92810-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92810-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="92810-104">Methods</span></span>  
  
|<span data-ttu-id="92810-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="92810-105">Method</span></span>|<span data-ttu-id="92810-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92810-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92810-107">CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92810-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="92810-108">CLR yeni oluşturduğunuz açıkça ister [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="92810-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="92810-109">GetCurrentTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92810-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="92810-110">Alır `ICLRTask` şu anda yürütülmekte olan görevi temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="92810-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="92810-111">GetCurrentTaskType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92810-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="92810-112">Şu anda yürütülmekte olan görevi türünü alır.</span><span class="sxs-lookup"><span data-stu-id="92810-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="92810-113">SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92810-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="92810-114">Konak şu anda yürütülmekte olan görevi yerel ayar tanımlayıcısı değiştirdi CLR bildirir.</span><span class="sxs-lookup"><span data-stu-id="92810-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="92810-115">SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92810-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="92810-116">Ortak dil çalışma zamanı ana kullanıcı arabirimi yerel ayar tanımlayıcısı şu anda yürütülen görevde değiştirdi bildirir.</span><span class="sxs-lookup"><span data-stu-id="92810-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92810-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92810-117">Remarks</span></span>  
 <span data-ttu-id="92810-118">Barındırılan bir ortamda çalışan her görev temsile her iki konak tarafında sahiptir (örneği [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) ve CLR tarafında (örneği [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="92810-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="92810-119">Konak veya CLR görev oluşturulmasını başlatabilir, ancak konak tarafı gösterimi konakla ilgili görev CLR arasındaki başarılı iletişim sağlamak için karşılık gelen bir CLR tarafı gösterimi ile ilişkilendirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="92810-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="92810-120">İki nesne oluşturulur ve bir işletim sistemi iş parçacığı üzerinde yönetilen kodu yürütmeden önce örneği.</span><span class="sxs-lookup"><span data-stu-id="92810-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92810-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92810-121">Requirements</span></span>  
 <span data-ttu-id="92810-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92810-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92810-123">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92810-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92810-124">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="92810-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92810-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92810-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92810-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92810-126">See also</span></span>

- [<span data-ttu-id="92810-127">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92810-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="92810-128">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92810-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="92810-129">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92810-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="92810-130">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="92810-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
