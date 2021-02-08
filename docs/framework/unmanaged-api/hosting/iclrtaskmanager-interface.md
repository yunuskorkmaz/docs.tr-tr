---
description: ': ICLRTaskManager arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0ce3641042725bc2f3acb95933ccd7a5bbe3bc4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789755"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="5f68e-103">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f68e-103">ICLRTaskManager Interface</span></span>

<span data-ttu-id="5f68e-104">Ana bilgisayarın ortak dil çalışma zamanının (CLR) yeni bir görev oluşturmasını, şu anda yürütülmekte olan görevi almasını ve görevin coğrafi dilini ve kültürünü ayarlamanızı sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f68e-104">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f68e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5f68e-105">Methods</span></span>  
  
|<span data-ttu-id="5f68e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5f68e-106">Method</span></span>|<span data-ttu-id="5f68e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f68e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f68e-108">CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f68e-108">CreateTask Method</span></span>](iclrtaskmanager-createtask-method.md)|<span data-ttu-id="5f68e-109">CLR 'nin yeni bir [ICLRTask](iclrtask-interface.md) örneği oluşturmasını açıkça ister.</span><span class="sxs-lookup"><span data-stu-id="5f68e-109">Requests explicitly that the CLR create a new [ICLRTask](iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="5f68e-110">GetCurrentTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f68e-110">GetCurrentTask Method</span></span>](iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="5f68e-111">`ICLRTask`Şu anda yürütülmekte olan görevi temsil eden örneği alır.</span><span class="sxs-lookup"><span data-stu-id="5f68e-111">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="5f68e-112">GetCurrentTaskType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f68e-112">GetCurrentTaskType Method</span></span>](iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="5f68e-113">Şu anda yürütülmekte olan görevin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="5f68e-113">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="5f68e-114">SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f68e-114">SetLocale Method</span></span>](iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="5f68e-115">, Konağın Şu anda yürütülmekte olan görevde yerel ayar tanıtıcısını değiştirdiğinizi CLR 'ye bildirir.</span><span class="sxs-lookup"><span data-stu-id="5f68e-115">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="5f68e-116">SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f68e-116">SetUILocale Method</span></span>](iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="5f68e-117">Ana bilgisayarın şu anda yürütülmekte olan görevde Kullanıcı arabirimi yerel ayar tanımlayıcısını değiştirdiği ortak dil çalışma zamanına bildirir.</span><span class="sxs-lookup"><span data-stu-id="5f68e-117">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f68e-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f68e-118">Remarks</span></span>  

 <span data-ttu-id="5f68e-119">Barındırılan bir ortamda çalışan her görev, hem konak tarafında (bir [IHostTask](ihosttask-interface.md)örneği) hem de clr tarafında ( [ICLRTask](iclrtask-interface.md)örneği) temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="5f68e-119">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](iclrtask-interface.md)).</span></span> <span data-ttu-id="5f68e-120">Konak veya CLR bir görevin oluşturulmasını başlatabilir, ancak konakla ilgili konak ile CLR arasında başarılı bir iletişim sağlamak için konak tarafı gösteriminin karşılık gelen bir CLR tarafı temsili ile ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f68e-120">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="5f68e-121">Yönetilen kodun bir işletim sistemi iş parçacığında yürütülebilmesi için önce iki nesnenin oluşturulup oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f68e-121">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f68e-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f68e-122">Requirements</span></span>  

 <span data-ttu-id="5f68e-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f68e-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f68e-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5f68e-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f68e-125">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5f68e-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f68e-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f68e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f68e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f68e-127">See also</span></span>

- [<span data-ttu-id="5f68e-128">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f68e-128">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="5f68e-129">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f68e-129">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5f68e-130">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f68e-130">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="5f68e-131">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5f68e-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
