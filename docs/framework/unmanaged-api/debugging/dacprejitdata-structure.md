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
ms.openlocfilehash: a2850add9acb2f7c5297ac6956e349c9277be291
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122804"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="0824e-102">DacpReJitData Yapısı</span><span class="sxs-lookup"><span data-stu-id="0824e-102">DacpReJitData Structure</span></span>

<span data-ttu-id="0824e-103">Belirli bir profil oluşturucu izleme eklenmiş yöntemi ile ilgili temel bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0824e-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0824e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0824e-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="0824e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0824e-105">Members</span></span>

| <span data-ttu-id="0824e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0824e-106">Member</span></span>           | <span data-ttu-id="0824e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0824e-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="0824e-108">Bir yöntem için ReJit düzeltme numarası.</span><span class="sxs-lookup"><span data-stu-id="0824e-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="0824e-109">Belirtilen sürüm için yöntemin ReJit izleme geçerli durumunu belirten bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="0824e-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="0824e-110">Yöntemin rejitted uygulamasının temel adres.</span><span class="sxs-lookup"><span data-stu-id="0824e-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="0824e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0824e-111">Remarks</span></span>

<span data-ttu-id="0824e-112">Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="0824e-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="0824e-113">Bunu kullanmak için yukarıda belirtildiği gibi yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0824e-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="0824e-114">Yapı kullanarak da tanımlanmalıdır `ms_struct` Microsoft derleyicileri kullanarak değilse paketleme.</span><span class="sxs-lookup"><span data-stu-id="0824e-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="0824e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0824e-115">Requirements</span></span>
<span data-ttu-id="0824e-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0824e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0824e-117">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="0824e-117">**Header:** None</span></span>  
<span data-ttu-id="0824e-118">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="0824e-118">**Library:** None</span></span>  
**<span data-ttu-id="0824e-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="0824e-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="0824e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0824e-120">See also</span></span>

- [<span data-ttu-id="0824e-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0824e-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="0824e-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="0824e-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
