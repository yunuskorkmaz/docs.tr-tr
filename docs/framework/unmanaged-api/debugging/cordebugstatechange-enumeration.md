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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05a29022d3ebad37322aef9826f10689d2b5b06b
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221140"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="5ee2f-102">CorDebugStateChange Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5ee2f-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="5ee2f-103">Değişiklikler iş akışına dayalı atılması gerekir önbelleğe alınan veri miktarı açıklar.</span><span class="sxs-lookup"><span data-stu-id="5ee2f-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ee2f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ee2f-104">Syntax</span></span>

```
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="5ee2f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5ee2f-105">Members</span></span>

| <span data-ttu-id="5ee2f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="5ee2f-106">Member</span></span>            | <span data-ttu-id="5ee2f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ee2f-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="5ee2f-108">İşlem, iletme yürütme aracılığıyla yeni bir bellek durumuna erişmedi.</span><span class="sxs-lookup"><span data-stu-id="5ee2f-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="5ee2f-109">İşlem bellek öncekinden rasgele farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5ee2f-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="5ee2f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ee2f-110">Remarks</span></span>

 <span data-ttu-id="5ee2f-111">Üye `CorDebugStateChange` numaralandırma hata ayıklayıcı çağırdığında bir bağımsız değişken olarak sağlanan `ProcessStateChanged` yöntemi ile birlikte [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) veya [Icordebugprocess6:: ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="5ee2f-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="5ee2f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ee2f-112">Requirements</span></span>

 <span data-ttu-id="5ee2f-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ee2f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="5ee2f-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ee2f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="5ee2f-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ee2f-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="5ee2f-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ee2f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5ee2f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ee2f-117">See also</span></span>

- [<span data-ttu-id="5ee2f-118">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="5ee2f-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="5ee2f-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5ee2f-119">Debugging</span></span>](index.md)
