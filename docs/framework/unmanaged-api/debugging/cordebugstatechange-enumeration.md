---
description: 'Daha fazla bilgi edinin: CorDebugStateChange numaralandırması'
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
ms.openlocfilehash: 1900baa77432daa10d0f1a32dd9cb25198b86ed1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661824"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="1c8e1-103">CorDebugStateChange Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1c8e1-103">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="1c8e1-104">İşlemdeki değişikliklere göre atılması gereken önbelleğe alınmış verilerin miktarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c8e1-104">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c8e1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1c8e1-105">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="1c8e1-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1c8e1-106">Members</span></span>

| <span data-ttu-id="1c8e1-107">Üye</span><span class="sxs-lookup"><span data-stu-id="1c8e1-107">Member</span></span>            | <span data-ttu-id="1c8e1-108">Description</span><span class="sxs-lookup"><span data-stu-id="1c8e1-108">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="1c8e1-109">İşlem, ileri yürütme yoluyla yeni bir bellek durumuna ulaştı.</span><span class="sxs-lookup"><span data-stu-id="1c8e1-109">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="1c8e1-110">İşlemin belleği daha önce gerekenden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c8e1-110">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="1c8e1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c8e1-111">Remarks</span></span>

 <span data-ttu-id="1c8e1-112">`CorDebugStateChange`Hata ayıklayıcı ICorDebugProcess4 ile yöntemi çağırdığında numaralandırma üyesi bir bağımsız değişken olarak sağlanır `ProcessStateChanged` [::P rocessstatechanged](icordebugprocess4-processstatechanged-method.md) veya [ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="1c8e1-112">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="1c8e1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c8e1-113">Requirements</span></span>

 <span data-ttu-id="1c8e1-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c8e1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="1c8e1-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1c8e1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="1c8e1-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1c8e1-116">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="1c8e1-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c8e1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1c8e1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c8e1-118">See also</span></span>

- [<span data-ttu-id="1c8e1-119">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="1c8e1-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="1c8e1-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1c8e1-120">Debugging</span></span>](index.md)
