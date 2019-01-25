---
title: ICLROnEventManager Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f927cece9997c78a75b1edecdb0a671203c3dd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646899"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="cddd8-102">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cddd8-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="cddd8-103">Kaydetme ve geri çağırmaları ortak dil çalışma zamanı (CLR) olaylarını kaydını silmek konak sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cddd8-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cddd8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cddd8-104">Methods</span></span>  
  
|<span data-ttu-id="cddd8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cddd8-105">Method</span></span>|<span data-ttu-id="cddd8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cddd8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cddd8-107">RegisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cddd8-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="cddd8-108">Bir geri çağırma işaretçi belirtilen olay için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cddd8-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="cddd8-109">UnregisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cddd8-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="cddd8-110">Belirtilen olay önceden kaydedilmiş bir geri çağırma işaretçi kaydını siler.</span><span class="sxs-lookup"><span data-stu-id="cddd8-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cddd8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cddd8-111">Remarks</span></span>  
 <span data-ttu-id="cddd8-112">Ana bilgisayar kaydetme ve olay geri çağırmaları kaydını silmek için bir başvuru edinir `ICLROnEventManager` çağırarak [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cddd8-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cddd8-113">Tarafından tanımlanan olayları [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) bir kaldırma veya CLR devre dışı bırakma sinyal farklı iş parçacıkları ve birden çok kez tetiklendi.</span><span class="sxs-lookup"><span data-stu-id="cddd8-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cddd8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cddd8-114">Requirements</span></span>  
 <span data-ttu-id="cddd8-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cddd8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cddd8-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cddd8-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cddd8-117">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cddd8-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cddd8-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cddd8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cddd8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cddd8-119">See also</span></span>
- [<span data-ttu-id="cddd8-120">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="cddd8-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="cddd8-121">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cddd8-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="cddd8-122">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cddd8-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="cddd8-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cddd8-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
