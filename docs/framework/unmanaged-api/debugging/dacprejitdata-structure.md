---
description: 'Daha fazla bilgi edinin: Dacprejdata yapısı'
title: DacpReJitData Yapısı
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 8e8d506856dbc6579ac6ea0eee2b2088a980a315
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801442"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="71d8a-103">DacpReJitData Yapısı</span><span class="sxs-lookup"><span data-stu-id="71d8a-103">DacpReJitData Structure</span></span>

<span data-ttu-id="71d8a-104">Belirli bir profil oluşturucu tarafından işaretlenmiş yöntem hakkında temel bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="71d8a-104">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="71d8a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="71d8a-105">Syntax</span></span>

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a><span data-ttu-id="71d8a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="71d8a-106">Members</span></span>

| <span data-ttu-id="71d8a-107">Üye</span><span class="sxs-lookup"><span data-stu-id="71d8a-107">Member</span></span>           | <span data-ttu-id="71d8a-108">Description</span><span class="sxs-lookup"><span data-stu-id="71d8a-108">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="71d8a-109">Bir yöntem için ReJIT düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="71d8a-109">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="71d8a-110">Metodun verilen sürüm için yeniden JIT araçlarının geçerli durumunu belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="71d8a-110">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="71d8a-111">Metodun yeniden derlenen uygulamasının temel adresi.</span><span class="sxs-lookup"><span data-stu-id="71d8a-111">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="71d8a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71d8a-112">Remarks</span></span>

<span data-ttu-id="71d8a-113">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="71d8a-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="71d8a-114">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="71d8a-114">To use it, define the structure as specified above.</span></span> <span data-ttu-id="71d8a-115">Yapının, Microsoft derleyicileri kullanılıyorsa paketleme kullanılarak da tanımlanması gerekir `ms_struct` .</span><span class="sxs-lookup"><span data-stu-id="71d8a-115">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="71d8a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71d8a-116">Requirements</span></span>

<span data-ttu-id="71d8a-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71d8a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="71d8a-118">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="71d8a-118">**Header:** None</span></span>  
<span data-ttu-id="71d8a-119">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="71d8a-119">**Library:** None</span></span>  
<span data-ttu-id="71d8a-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="71d8a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="71d8a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71d8a-121">See also</span></span>

- [<span data-ttu-id="71d8a-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="71d8a-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="71d8a-123">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="71d8a-123">Debugging Structures</span></span>](debugging-structures.md)
