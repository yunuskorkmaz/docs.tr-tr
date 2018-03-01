---
title: ICLRTaskManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 342d7b82802fcfbe9e179d85d6d692205f19e382
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="29624-102">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29624-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="29624-103">Ortak dil çalışma zamanı (CLR) açıkça istemek için ana izin yöntemleri yeni bir görev oluşturma, şu anda yürütülen görev almak ve coğrafi dil ve kültür görev için ayarlanmış sağlar.</span><span class="sxs-lookup"><span data-stu-id="29624-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29624-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="29624-104">Methods</span></span>  
  
|<span data-ttu-id="29624-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="29624-105">Method</span></span>|<span data-ttu-id="29624-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29624-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29624-107">CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29624-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="29624-108">Açıkça CLR yenisini oluşturmak ister [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="29624-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="29624-109">GetCurrentTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29624-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="29624-110">Alır `ICLRTask` şu anda yürütülmekte görev temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="29624-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="29624-111">GetCurrentTaskType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29624-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="29624-112">Şu anda yürütülmekte görevi türünü alır.</span><span class="sxs-lookup"><span data-stu-id="29624-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="29624-113">SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29624-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="29624-114">Konak şu anda yürütülen görevde yerel ayar tanımlayıcısı değiştirdi CLR bildirir.</span><span class="sxs-lookup"><span data-stu-id="29624-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="29624-115">SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29624-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="29624-116">Ortak dil çalışma zamanı ana bilgisayar şu anda yürütülen görev kullanıcı arabirimi yerel ayar tanımlayıcısı değiştirdi bildirir.</span><span class="sxs-lookup"><span data-stu-id="29624-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29624-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29624-117">Remarks</span></span>  
 <span data-ttu-id="29624-118">Barındırılan bir ortamda çalışan her görev Beyanları hem ana bilgisayar tarafında vardır (bir örneği [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) ve CLR tarafında (örneği [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="29624-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="29624-119">Ana bilgisayar veya CLR bir görevi oluşturma işlemi başlatabilir, ancak ana bilgisayar tarafı gösterimi konak ve ilgili görev CLR arasındaki başarılı iletişim sağlamak için karşılık gelen bir CLR tarafı gösterimi ile ilişkilendirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="29624-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="29624-120">İki nesne oluşturulan ve yönetilen kod bir işletim sistemi iş parçacığına yürütebilir önce örneği.</span><span class="sxs-lookup"><span data-stu-id="29624-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29624-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29624-121">Requirements</span></span>  
 <span data-ttu-id="29624-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29624-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29624-123">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="29624-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29624-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="29624-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29624-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29624-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29624-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29624-126">See Also</span></span>  
 [<span data-ttu-id="29624-127">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29624-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="29624-128">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29624-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="29624-129">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29624-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="29624-130">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="29624-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
