---
title: CorDebugDecodeEventFlagsWindows Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99283200a4e9af2e9232b6ce6c25702f47a5cc42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510214"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="67605-102">CorDebugDecodeEventFlagsWindows Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="67605-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="67605-103">Hata ayıklama olaylar hakkında ek bilgi için Windows platformunda sağlar.</span><span class="sxs-lookup"><span data-stu-id="67605-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67605-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67605-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="67605-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="67605-105">Members</span></span>  
  
|<span data-ttu-id="67605-106">Üye</span><span class="sxs-lookup"><span data-stu-id="67605-106">Member</span></span>|<span data-ttu-id="67605-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67605-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="67605-108">Hata ayıklama olayı ilk fırsat özel durum olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="67605-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67605-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67605-109">Remarks</span></span>  
 <span data-ttu-id="67605-110">[Icordebugprocess6::decodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi içeren bir `dwFlags` hata ayıklama olay hakkında ek bilgi sağlayan ve değeri hedef mimarisine bağımlı olan parametre.</span><span class="sxs-lookup"><span data-stu-id="67605-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="67605-111">`CorDebugDecodeEventFlagsWindows` Numaralandırma, Windows platformunda hata ayıklama olayları ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67605-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67605-112">Bu numaralandırma .NET hata ayıklama senaryoları yalnızca yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="67605-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67605-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67605-113">Requirements</span></span>  
 <span data-ttu-id="67605-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67605-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67605-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67605-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67605-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67605-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67605-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67605-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67605-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67605-118">See also</span></span>
- [<span data-ttu-id="67605-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="67605-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
