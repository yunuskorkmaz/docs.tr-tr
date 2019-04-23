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
ms.openlocfilehash: 7486a094deab16ebbc05f19f1b652126479ce11c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183007"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="3bd70-102">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bd70-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="3bd70-103">Kaydetme ve geri çağırmaları ortak dil çalışma zamanı (CLR) olaylarını kaydını silmek konak sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3bd70-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3bd70-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3bd70-104">Methods</span></span>  
  
|<span data-ttu-id="3bd70-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3bd70-105">Method</span></span>|<span data-ttu-id="3bd70-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bd70-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3bd70-107">RegisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3bd70-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="3bd70-108">Bir geri çağırma işaretçi belirtilen olay için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3bd70-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="3bd70-109">UnregisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3bd70-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="3bd70-110">Belirtilen olay önceden kaydedilmiş bir geri çağırma işaretçi kaydını siler.</span><span class="sxs-lookup"><span data-stu-id="3bd70-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bd70-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3bd70-111">Remarks</span></span>  
 <span data-ttu-id="3bd70-112">Ana bilgisayar kaydetme ve olay geri çağırmaları kaydını silmek için bir başvuru edinir `ICLROnEventManager` çağırarak [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3bd70-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bd70-113">Tarafından tanımlanan olayları [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) bir kaldırma veya CLR devre dışı bırakma sinyal farklı iş parçacıkları ve birden çok kez tetiklendi.</span><span class="sxs-lookup"><span data-stu-id="3bd70-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bd70-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3bd70-114">Requirements</span></span>  
 <span data-ttu-id="3bd70-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bd70-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bd70-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3bd70-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3bd70-117">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3bd70-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3bd70-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bd70-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bd70-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bd70-119">See also</span></span>

- [<span data-ttu-id="3bd70-120">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3bd70-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="3bd70-121">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bd70-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="3bd70-122">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bd70-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="3bd70-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3bd70-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
