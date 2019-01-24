---
title: CorDebugStateChange Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f0f692b692628d50755ce813c66823f940dccb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513795"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="e348c-102">CorDebugStateChange Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e348c-102">CorDebugStateChange Enumeration</span></span>
<span data-ttu-id="e348c-103">Değişiklikler iş akışına dayalı atılması gerekir önbelleğe alınan veri miktarı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e348c-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e348c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e348c-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a><span data-ttu-id="e348c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e348c-105">Members</span></span>  
  
|<span data-ttu-id="e348c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e348c-106">Member</span></span>|<span data-ttu-id="e348c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e348c-107">Description</span></span>|  
|------------|-----------------|  
|`PROCESS_RUNNING`|<span data-ttu-id="e348c-108">İşlem, iletme yürütme aracılığıyla yeni bir bellek durumuna erişmedi.</span><span class="sxs-lookup"><span data-stu-id="e348c-108">The process reached a new memory state via forward execution.</span></span>|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|<span data-ttu-id="e348c-109">İşlem bellek öncekinden rasgele farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e348c-109">The process' memory may be arbitrarily different than it was previously.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e348c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e348c-110">Remarks</span></span>  
 <span data-ttu-id="e348c-111">Üye `CorDebugStateChange` numaralandırma hata ayıklayıcı çağırdığında bir bağımsız değişken olarak sağlanan [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) yöntemi</span><span class="sxs-lookup"><span data-stu-id="e348c-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) method</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e348c-112">Bu numaralandırma .NET hata ayıklama senaryoları yalnızca yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e348c-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e348c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e348c-113">Requirements</span></span>  
 <span data-ttu-id="e348c-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e348c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e348c-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e348c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e348c-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e348c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e348c-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e348c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e348c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e348c-118">See also</span></span>
- [<span data-ttu-id="e348c-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e348c-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="e348c-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e348c-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
