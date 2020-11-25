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
ms.openlocfilehash: 1170b29c01275b108a6ccdf6e324c96d97c10c82
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732456"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="e414e-102">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e414e-102">ICLRTaskManager Interface</span></span>

<span data-ttu-id="e414e-103">Ana bilgisayarın ortak dil çalışma zamanının (CLR) yeni bir görev oluşturmasını, şu anda yürütülmekte olan görevi almasını ve görevin coğrafi dilini ve kültürünü ayarlamanızı sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e414e-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e414e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e414e-104">Methods</span></span>  
  
|<span data-ttu-id="e414e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e414e-105">Method</span></span>|<span data-ttu-id="e414e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e414e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e414e-107">CreateTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e414e-107">CreateTask Method</span></span>](iclrtaskmanager-createtask-method.md)|<span data-ttu-id="e414e-108">CLR 'nin yeni bir [ICLRTask](iclrtask-interface.md) örneği oluşturmasını açıkça ister.</span><span class="sxs-lookup"><span data-stu-id="e414e-108">Requests explicitly that the CLR create a new [ICLRTask](iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="e414e-109">GetCurrentTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e414e-109">GetCurrentTask Method</span></span>](iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="e414e-110">`ICLRTask`Şu anda yürütülmekte olan görevi temsil eden örneği alır.</span><span class="sxs-lookup"><span data-stu-id="e414e-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="e414e-111">GetCurrentTaskType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e414e-111">GetCurrentTaskType Method</span></span>](iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="e414e-112">Şu anda yürütülmekte olan görevin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="e414e-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="e414e-113">SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e414e-113">SetLocale Method</span></span>](iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="e414e-114">, Konağın Şu anda yürütülmekte olan görevde yerel ayar tanıtıcısını değiştirdiğinizi CLR 'ye bildirir.</span><span class="sxs-lookup"><span data-stu-id="e414e-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="e414e-115">SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e414e-115">SetUILocale Method</span></span>](iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="e414e-116">Ana bilgisayarın şu anda yürütülmekte olan görevde Kullanıcı arabirimi yerel ayar tanımlayıcısını değiştirdiği ortak dil çalışma zamanına bildirir.</span><span class="sxs-lookup"><span data-stu-id="e414e-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e414e-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e414e-117">Remarks</span></span>  

 <span data-ttu-id="e414e-118">Barındırılan bir ortamda çalışan her görev, hem konak tarafında (bir [IHostTask](ihosttask-interface.md)örneği) hem de clr tarafında ( [ICLRTask](iclrtask-interface.md)örneği) temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="e414e-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](iclrtask-interface.md)).</span></span> <span data-ttu-id="e414e-119">Konak veya CLR bir görevin oluşturulmasını başlatabilir, ancak konakla ilgili konak ile CLR arasında başarılı bir iletişim sağlamak için konak tarafı gösteriminin karşılık gelen bir CLR tarafı temsili ile ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e414e-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="e414e-120">Yönetilen kodun bir işletim sistemi iş parçacığında yürütülebilmesi için önce iki nesnenin oluşturulup oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e414e-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e414e-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e414e-121">Requirements</span></span>  

 <span data-ttu-id="e414e-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e414e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e414e-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e414e-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e414e-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e414e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e414e-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e414e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e414e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e414e-126">See also</span></span>

- [<span data-ttu-id="e414e-127">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e414e-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="e414e-128">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e414e-128">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="e414e-129">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e414e-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="e414e-130">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e414e-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
