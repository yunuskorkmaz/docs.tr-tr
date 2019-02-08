---
title: DacpReJitData Structure
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
ms.openlocfilehash: 974b99da085a5cb969ab37cddb0f2f2c62010d14
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828561"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="204b3-102">DacpReJitData Structure</span><span class="sxs-lookup"><span data-stu-id="204b3-102">DacpReJitData Structure</span></span>

<span data-ttu-id="204b3-103">Belirli bir profil oluşturucu izleme eklenmiş yöntemi ile ilgili temel bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="204b3-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="204b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="204b3-104">Syntax</span></span>

```
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

## <a name="members"></a><span data-ttu-id="204b3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="204b3-105">Members</span></span>

| <span data-ttu-id="204b3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="204b3-106">Member</span></span>           | <span data-ttu-id="204b3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="204b3-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="204b3-108">Bir yöntem için ReJit düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="204b3-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="204b3-109">Belirtilen sürüm için yöntemin ReJit izleme geçerli durumunu belirten bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="204b3-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="204b3-110">Yöntemin rejitted uygulamasının temel adres.</span><span class="sxs-lookup"><span data-stu-id="204b3-110">The base address of the method's rejitted implementation.</span></span>                                         |


## <a name="remarks"></a><span data-ttu-id="204b3-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="204b3-111">Remarks</span></span>

<span data-ttu-id="204b3-112">Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="204b3-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="204b3-113">Bunu kullanmak için yukarıda belirtildiği gibi yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="204b3-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="204b3-114">Yapı kullanarak da tanımlanmalıdır `ms_struct` Microsoft derleyicileri kullanarak değilse paketleme.</span><span class="sxs-lookup"><span data-stu-id="204b3-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="204b3-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="204b3-115">Requirements</span></span>
<span data-ttu-id="204b3-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="204b3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="204b3-117">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="204b3-117">**Header:** None</span></span>  
<span data-ttu-id="204b3-118">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="204b3-118">**Library:** None</span></span>  
<span data-ttu-id="204b3-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="204b3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="204b3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="204b3-120">See also</span></span>
- [<span data-ttu-id="204b3-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="204b3-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="204b3-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="204b3-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
