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
ms.openlocfilehash: 4436ece72b0a6a405fc41cba5413093fc42ce750
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860771"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="852c8-102">DacpReJitData Yapısı</span><span class="sxs-lookup"><span data-stu-id="852c8-102">DacpReJitData Structure</span></span>

<span data-ttu-id="852c8-103">Belirli bir profil oluşturucu tarafından işaretlenmiş yöntem hakkında temel bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="852c8-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="852c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="852c8-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="852c8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="852c8-105">Members</span></span>

| <span data-ttu-id="852c8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="852c8-106">Member</span></span>           | <span data-ttu-id="852c8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="852c8-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="852c8-108">Bir yöntem için ReJIT düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="852c8-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="852c8-109">Metodun verilen sürüm için yeniden JIT araçlarının geçerli durumunu belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="852c8-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="852c8-110">Metodun yeniden derlenen uygulamasının temel adresi.</span><span class="sxs-lookup"><span data-stu-id="852c8-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="852c8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="852c8-111">Remarks</span></span>

<span data-ttu-id="852c8-112">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="852c8-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="852c8-113">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="852c8-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="852c8-114">Yapının, Microsoft derleyicileri kullanılıyorsa paketleme `ms_struct` kullanılarak da tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="852c8-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="852c8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="852c8-115">Requirements</span></span>
<span data-ttu-id="852c8-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="852c8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="852c8-117">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="852c8-117">**Header:** None</span></span>  
<span data-ttu-id="852c8-118">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="852c8-118">**Library:** None</span></span>  
<span data-ttu-id="852c8-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="852c8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="852c8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="852c8-120">See also</span></span>

- [<span data-ttu-id="852c8-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="852c8-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="852c8-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="852c8-122">Debugging Structures</span></span>](debugging-structures.md)
