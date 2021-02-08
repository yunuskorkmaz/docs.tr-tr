---
description: 'Daha fazla bilgi edinin: EClrEvent numaralandırması'
title: EClrEvent Numaralandırması
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: 7c2365d1a2fb0109bab9159c3af4e2da3a46de6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785607"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="44196-103">EClrEvent Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="44196-103">EClrEvent Enumeration</span></span>

<span data-ttu-id="44196-104">Konağın geri çağırmaları kaydedebileceği ortak dil çalışma zamanı (CLR) olaylarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="44196-104">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44196-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="44196-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="44196-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="44196-106">Members</span></span>  
  
|<span data-ttu-id="44196-107">Üye</span><span class="sxs-lookup"><span data-stu-id="44196-107">Member</span></span>|<span data-ttu-id="44196-108">Description</span><span class="sxs-lookup"><span data-stu-id="44196-108">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="44196-109">Önemli bir CLR hatası belirtir.</span><span class="sxs-lookup"><span data-stu-id="44196-109">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="44196-110">Belirli bir sürümü kaldırmayı belirtir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="44196-110">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="44196-111">Yönetilen hata ayıklama Yardımcısı (MDA) iletisinin oluşturulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="44196-111">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="44196-112">Yığın taşması hatası oluştuğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="44196-112">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44196-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44196-113">Remarks</span></span>  

 <span data-ttu-id="44196-114">Konak, `EClrEvent` [ICLROnEventManager](iclroneventmanager-interface.md) arabiriminin yöntemlerini çağırarak tarafından tanımlanan olay türlerinden herhangi biri için geri çağırmaları kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="44196-114">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="44196-115">Ana bilgisayar [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) metodunu çağırarak bu arabirime yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="44196-115">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="44196-116">`Event_CLRDisabled`Ve `Event_DomainUnload` olayları bir defadan fazla ve farklı iş parçacıklarından bir KALDıRMA veya clr 'nin devre dışı bırakılmasını bildirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="44196-116">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="44196-117">`Event_MDAFired`Olay, MDA iletisinin ayrıntılarını içeren bir [Mdadınfo](mdainfo-structure.md) örneği oluşturulmasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="44196-117">The `Event_MDAFired` event raises the creation of an [MDAInfo](mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="44196-118">MDAs hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="44196-118">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44196-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44196-119">Requirements</span></span>  

 <span data-ttu-id="44196-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44196-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44196-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="44196-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44196-122">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44196-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44196-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44196-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44196-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44196-124">See also</span></span>

- [<span data-ttu-id="44196-125">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44196-125">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="44196-126">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44196-126">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="44196-127">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="44196-127">Hosting Enumerations</span></span>](hosting-enumerations.md)
