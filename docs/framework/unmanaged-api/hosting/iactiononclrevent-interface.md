---
title: IActionOnCLREvent Arabirimi
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: 8ca4bb1fe35451f95f752a4e71f5f0b541b55e58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721783"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="44d98-102">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44d98-102">IActionOnCLREvent Interface</span></span>

<span data-ttu-id="44d98-103">[ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) metoduna yapılan bir çağrı kullanılarak kaydedilmiş olaylarda geri çağırmaları gerçekleştiren [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) metodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="44d98-103">Provides the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="44d98-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="44d98-104">Methods</span></span>  
  
|<span data-ttu-id="44d98-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="44d98-105">Method</span></span>|<span data-ttu-id="44d98-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44d98-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="44d98-107">OnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="44d98-107">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="44d98-108">Kayıtlı bir olay için geri arama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="44d98-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44d98-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44d98-109">Requirements</span></span>  

 <span data-ttu-id="44d98-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44d98-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44d98-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="44d98-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44d98-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="44d98-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44d98-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44d98-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d98-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44d98-114">See also</span></span>

- [<span data-ttu-id="44d98-115">EClrEvent Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="44d98-115">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="44d98-116">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44d98-116">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="44d98-117">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44d98-117">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="44d98-118">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="44d98-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
