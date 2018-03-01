---
title: ICLROnEventManager Arabirimi
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
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 02a19a3daf72cdfa493b09fa984fe7b50865ed30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="c476a-102">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c476a-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="c476a-103">Kaydolun ve ortak dil çalışma zamanı (CLR) olayları için geri çağırmaları kaydı için ana izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c476a-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c476a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c476a-104">Methods</span></span>  
  
|<span data-ttu-id="c476a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c476a-105">Method</span></span>|<span data-ttu-id="c476a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c476a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c476a-107">RegisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c476a-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="c476a-108">Belirtilen olay için bir geri çağırma işaretçi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c476a-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="c476a-109">UnregisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c476a-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="c476a-110">Belirtilen olay için daha önce kaydedilmiş geri işaretçi kaydını siler.</span><span class="sxs-lookup"><span data-stu-id="c476a-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c476a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c476a-111">Remarks</span></span>  
 <span data-ttu-id="c476a-112">Konak kaydetmek ve olay geri aramalar kaydı için bir başvuru edinir `ICLROnEventManager` çağırarak [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c476a-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c476a-113">Tarafından tanımlanan olayları [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) birden çok kez ve bir kaldırma veya CLR devre dışı bırakma sinyal için farklı iş parçacıklarından tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="c476a-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c476a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c476a-114">Requirements</span></span>  
 <span data-ttu-id="c476a-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c476a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c476a-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c476a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c476a-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c476a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c476a-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c476a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c476a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c476a-119">See Also</span></span>  
 [<span data-ttu-id="c476a-120">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c476a-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="c476a-121">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c476a-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="c476a-122">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c476a-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="c476a-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c476a-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
