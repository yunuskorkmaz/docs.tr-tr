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
ms.openlocfilehash: 1948075d87b5a44397a1eaab3adb4edbc96d7143
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725644"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="0f8aa-102">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f8aa-102">ICLROnEventManager Interface</span></span>

<span data-ttu-id="0f8aa-103">Ana bilgisayarın ortak dil çalışma zamanı (CLR) olayları için geri çağırmaları kaydetmesine ve kaydını kaydetmesine izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f8aa-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f8aa-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0f8aa-104">Methods</span></span>  
  
|<span data-ttu-id="0f8aa-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0f8aa-105">Method</span></span>|<span data-ttu-id="0f8aa-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f8aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f8aa-107">RegisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f8aa-107">RegisterActionOnEvent Method</span></span>](iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="0f8aa-108">Belirtilen olay için bir geri çağırma işaretçisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0f8aa-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="0f8aa-109">UnregisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f8aa-109">UnregisterActionOnEvent Method</span></span>](iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="0f8aa-110">Belirtilen olay için önceden kaydedilmiş bir geri çağırma işaretçisinin kaydını siler.</span><span class="sxs-lookup"><span data-stu-id="0f8aa-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f8aa-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f8aa-111">Remarks</span></span>  

 <span data-ttu-id="0f8aa-112">Olay geri çağırmaları kaydetmek ve kaydını silmek için, ana bilgisayar `ICLROnEventManager` [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) metodunu çağırarak öğesine bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="0f8aa-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f8aa-113">[EClrEvent](eclrevent-enumeration.md) tarafından tanımlanan olaylar birden çok kez tetiklenebilir ve farklı iş PARÇACıKLARıNDAN clr 'nin kaldırılmasına veya devre dışı bırakılmasına işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="0f8aa-113">The events described by [EClrEvent](eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f8aa-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f8aa-114">Requirements</span></span>  

 <span data-ttu-id="0f8aa-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f8aa-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f8aa-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0f8aa-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f8aa-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0f8aa-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f8aa-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f8aa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f8aa-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f8aa-119">See also</span></span>

- [<span data-ttu-id="0f8aa-120">EClrEvent Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0f8aa-120">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="0f8aa-121">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f8aa-121">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="0f8aa-122">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f8aa-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="0f8aa-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0f8aa-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
