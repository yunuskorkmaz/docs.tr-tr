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
ms.openlocfilehash: 841108457293e3377ee87f9c7d7c6898340e51b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404352"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="81ca5-102">CorDebugStateChange Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="81ca5-102">CorDebugStateChange Enumeration</span></span>
<span data-ttu-id="81ca5-103">Değişiklikleri işleme dayalı atılan gerekir önbelleğe alınan veri miktarı açıklar.</span><span class="sxs-lookup"><span data-stu-id="81ca5-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81ca5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81ca5-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a><span data-ttu-id="81ca5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="81ca5-105">Members</span></span>  
  
|<span data-ttu-id="81ca5-106">Üye</span><span class="sxs-lookup"><span data-stu-id="81ca5-106">Member</span></span>|<span data-ttu-id="81ca5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81ca5-107">Description</span></span>|  
|------------|-----------------|  
|`PROCESS_RUNNING`|<span data-ttu-id="81ca5-108">İşlem ileriye doğru yürütme aracılığıyla yeni bir bellek durum sınırına ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="81ca5-108">The process reached a new memory state via forward execution.</span></span>|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|<span data-ttu-id="81ca5-109">İşlem bellek öncekinden daha rasgele farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="81ca5-109">The process' memory may be arbitrarily different than it was previously.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81ca5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81ca5-110">Remarks</span></span>  
 <span data-ttu-id="81ca5-111">Üye `CorDebugStateChange` numaralandırma, bağımsız değişken olarak sağlanır, hata ayıklayıcı çağırdığında [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) yöntemi</span><span class="sxs-lookup"><span data-stu-id="81ca5-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) method</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81ca5-112">Bu numaralandırma .NET senaryoları yalnızca hata ayıklama yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="81ca5-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81ca5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81ca5-113">Requirements</span></span>  
 <span data-ttu-id="81ca5-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81ca5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81ca5-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81ca5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81ca5-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81ca5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81ca5-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81ca5-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ca5-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81ca5-118">See Also</span></span>  
 [<span data-ttu-id="81ca5-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="81ca5-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="81ca5-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="81ca5-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
