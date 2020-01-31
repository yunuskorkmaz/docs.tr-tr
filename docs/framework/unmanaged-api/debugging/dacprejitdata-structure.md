---
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
ms.openlocfilehash: 46031f29da6916eeaeea863ebef6924a720d7155
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793824"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="e244e-102">DacpReJitData Yapısı</span><span class="sxs-lookup"><span data-stu-id="e244e-102">DacpReJitData Structure</span></span>

<span data-ttu-id="e244e-103">Belirli bir profil oluşturucu tarafından işaretlenmiş yöntem hakkında temel bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e244e-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e244e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e244e-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="e244e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e244e-105">Members</span></span>

| <span data-ttu-id="e244e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e244e-106">Member</span></span>           | <span data-ttu-id="e244e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e244e-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="e244e-108">Bir yöntem için ReJIT düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="e244e-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="e244e-109">Metodun verilen sürüm için yeniden JIT araçlarının geçerli durumunu belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="e244e-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="e244e-110">Metodun yeniden derlenen uygulamasının temel adresi.</span><span class="sxs-lookup"><span data-stu-id="e244e-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="e244e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e244e-111">Remarks</span></span>

<span data-ttu-id="e244e-112">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="e244e-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="e244e-113">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e244e-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="e244e-114">Yapının ayrıca Microsoft derleyicileri yoksa `ms_struct` paketleme kullanılarak tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e244e-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="e244e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e244e-115">Requirements</span></span>
<span data-ttu-id="e244e-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e244e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e244e-117">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="e244e-117">**Header:** None</span></span>  
<span data-ttu-id="e244e-118">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="e244e-118">**Library:** None</span></span>  
<span data-ttu-id="e244e-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e244e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e244e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e244e-120">See also</span></span>

- [<span data-ttu-id="e244e-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e244e-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="e244e-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="e244e-122">Debugging Structures</span></span>](debugging-structures.md)
