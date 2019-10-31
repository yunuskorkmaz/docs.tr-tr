---
title: CorDebugStateChange Numaralandırması
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
ms.openlocfilehash: 239e3a82df0e6010278669f9f429bfad0d163319
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133719"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="7aebd-102">CorDebugStateChange Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7aebd-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="7aebd-103">İşlemdeki değişikliklere göre atılması gereken önbelleğe alınmış verilerin miktarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7aebd-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="7aebd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7aebd-104">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="7aebd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7aebd-105">Members</span></span>

| <span data-ttu-id="7aebd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7aebd-106">Member</span></span>            | <span data-ttu-id="7aebd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7aebd-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="7aebd-108">İşlem, ileri yürütme yoluyla yeni bir bellek durumuna ulaştı.</span><span class="sxs-lookup"><span data-stu-id="7aebd-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="7aebd-109">İşlemin belleği daha önce gerekenden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7aebd-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7aebd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7aebd-110">Remarks</span></span>

 <span data-ttu-id="7aebd-111">Hata ayıklayıcı, `ProcessStateChanged` yöntemini [ICorDebugProcess4::P rocessstatechanged](icordebugprocess4-processstatechanged-method.md) veya [ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md) ile çağırdığında `CorDebugStateChange` numaralandırmanın bir üyesi olarak sağlanır</span><span class="sxs-lookup"><span data-stu-id="7aebd-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="7aebd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7aebd-112">Requirements</span></span>

 <span data-ttu-id="7aebd-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aebd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="7aebd-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7aebd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="7aebd-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7aebd-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="7aebd-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aebd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7aebd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7aebd-117">See also</span></span>

- [<span data-ttu-id="7aebd-118">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7aebd-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="7aebd-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7aebd-119">Debugging</span></span>](index.md)
