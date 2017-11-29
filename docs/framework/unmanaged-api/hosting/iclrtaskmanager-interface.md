---
title: ICLRTaskManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager
helpviewer_keywords: ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3144338ddce262aaa6772f588a4f1a652cc57e01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="a78dd-102">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a78dd-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="a78dd-103">Ortak dil çalışma zamanı (CLR) açıkça istemek için ana izin yöntemleri yeni bir görev oluşturma, şu anda yürütülen görev almak ve coğrafi dil ve kültür görev için ayarlanmış sağlar.</span><span class="sxs-lookup"><span data-stu-id="a78dd-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a78dd-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a78dd-104">Methods</span></span>  
  
|<span data-ttu-id="a78dd-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a78dd-105">Method</span></span>|<span data-ttu-id="a78dd-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a78dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a78dd-107">CreateTask yöntemi</span><span class="sxs-lookup"><span data-stu-id="a78dd-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="a78dd-108">Açıkça CLR yenisini oluşturmak ister [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="a78dd-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="a78dd-109">GetCurrentTask yöntemi</span><span class="sxs-lookup"><span data-stu-id="a78dd-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="a78dd-110">Alır `ICLRTask` şu anda yürütülmekte görev temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="a78dd-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="a78dd-111">GetCurrentTaskType yöntemi</span><span class="sxs-lookup"><span data-stu-id="a78dd-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="a78dd-112">Şu anda yürütülmekte görevi türünü alır.</span><span class="sxs-lookup"><span data-stu-id="a78dd-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="a78dd-113">SetLocale yöntemi</span><span class="sxs-lookup"><span data-stu-id="a78dd-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="a78dd-114">Konak şu anda yürütülen görevde yerel ayar tanımlayıcısı değiştirdi CLR bildirir.</span><span class="sxs-lookup"><span data-stu-id="a78dd-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="a78dd-115">Setuılocale yöntemi</span><span class="sxs-lookup"><span data-stu-id="a78dd-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="a78dd-116">Ortak dil çalışma zamanı ana bilgisayar şu anda yürütülen görev kullanıcı arabirimi yerel ayar tanımlayıcısı değiştirdi bildirir.</span><span class="sxs-lookup"><span data-stu-id="a78dd-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a78dd-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a78dd-117">Remarks</span></span>  
 <span data-ttu-id="a78dd-118">Barındırılan bir ortamda çalışan her görev Beyanları hem ana bilgisayar tarafında vardır (bir örneği [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) ve CLR tarafında (örneği [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="a78dd-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="a78dd-119">Ana bilgisayar veya CLR bir görevi oluşturma işlemi başlatabilir, ancak ana bilgisayar tarafı gösterimi konak ve ilgili görev CLR arasındaki başarılı iletişim sağlamak için karşılık gelen bir CLR tarafı gösterimi ile ilişkilendirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a78dd-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="a78dd-120">İki nesne oluşturulan ve yönetilen kod bir işletim sistemi iş parçacığına yürütebilir önce örneği.</span><span class="sxs-lookup"><span data-stu-id="a78dd-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a78dd-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a78dd-121">Requirements</span></span>  
 <span data-ttu-id="a78dd-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a78dd-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a78dd-123">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a78dd-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a78dd-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a78dd-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a78dd-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a78dd-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a78dd-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a78dd-126">See Also</span></span>  
 [<span data-ttu-id="a78dd-127">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="a78dd-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a78dd-128">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="a78dd-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a78dd-129">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="a78dd-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="a78dd-130">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a78dd-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
