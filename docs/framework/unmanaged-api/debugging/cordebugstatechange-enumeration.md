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
ms.openlocfilehash: d94422d25da91cd2a6653a95cbd852c3930a151a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795696"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="385ee-102">CorDebugStateChange Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="385ee-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="385ee-103">İşlemdeki değişikliklere göre atılması gereken önbelleğe alınmış verilerin miktarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="385ee-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="385ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="385ee-104">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="385ee-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="385ee-105">Members</span></span>

| <span data-ttu-id="385ee-106">Üye</span><span class="sxs-lookup"><span data-stu-id="385ee-106">Member</span></span>            | <span data-ttu-id="385ee-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="385ee-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="385ee-108">İşlem, ileri yürütme yoluyla yeni bir bellek durumuna ulaştı.</span><span class="sxs-lookup"><span data-stu-id="385ee-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="385ee-109">İşlemin belleği daha önce gerekenden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="385ee-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="385ee-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="385ee-110">Remarks</span></span>

 <span data-ttu-id="385ee-111">Hata ayıklayıcı ICorDebugProcess4 ile `CorDebugStateChange` `ProcessStateChanged` yöntemi çağırdığında numaralandırma üyesi bir bağımsız değişken olarak sağlanır [::P Rocessstatechanged](icordebugprocess4-processstatechanged-method.md) veya [ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="385ee-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="385ee-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="385ee-112">Requirements</span></span>

 <span data-ttu-id="385ee-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="385ee-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="385ee-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="385ee-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="385ee-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="385ee-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="385ee-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="385ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="385ee-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="385ee-117">See also</span></span>

- [<span data-ttu-id="385ee-118">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="385ee-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="385ee-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="385ee-119">Debugging</span></span>](index.md)
