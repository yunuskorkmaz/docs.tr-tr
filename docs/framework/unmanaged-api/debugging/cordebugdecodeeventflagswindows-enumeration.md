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
ms.openlocfilehash: da3a100bd552eaa3233642b006e0265adbcac1ca
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132208"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="44dd2-102">CorDebugDecodeEventFlagsWindows Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="44dd2-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="44dd2-103">Windows platformunda hata ayıklama olayları hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="44dd2-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44dd2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44dd2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="44dd2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="44dd2-105">Members</span></span>  
  
|<span data-ttu-id="44dd2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="44dd2-106">Member</span></span>|<span data-ttu-id="44dd2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44dd2-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="44dd2-108">Hata ayıklama olayının ilk şans özel durumu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="44dd2-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44dd2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44dd2-109">Remarks</span></span>  
 <span data-ttu-id="44dd2-110">[ICorDebugProcess6::D ecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi, bir hata ayıklama olayı ve değeri hedef mimarisine bağlı olan ek bilgiler sağlayan bir `dwFlags` parametresi içerir.</span><span class="sxs-lookup"><span data-stu-id="44dd2-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="44dd2-111">`CorDebugDecodeEventFlagsWindows` numaralandırması, Windows platformunda hata ayıklama olayları ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="44dd2-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44dd2-112">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="44dd2-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44dd2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44dd2-113">Requirements</span></span>  
 <span data-ttu-id="44dd2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44dd2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44dd2-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="44dd2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44dd2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="44dd2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44dd2-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44dd2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44dd2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44dd2-118">See also</span></span>

- [<span data-ttu-id="44dd2-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="44dd2-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
