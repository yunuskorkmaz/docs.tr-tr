---
description: 'Daha fazla bilgi edinin: Davcpmethoddescdata yapısı'
title: DacpMethodDescData Yapısı
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: fe5b09874b3f8e123cb2501fcb00e3351aa44757
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801468"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="7705a-103">DacpMethodDescData Yapısı</span><span class="sxs-lookup"><span data-stu-id="7705a-103">DacpMethodDescData Structure</span></span>

<span data-ttu-id="7705a-104">Metodun çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7705a-104">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7705a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7705a-105">Syntax</span></span>

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a><span data-ttu-id="7705a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7705a-106">Members</span></span>

| <span data-ttu-id="7705a-107">Üye</span><span class="sxs-lookup"><span data-stu-id="7705a-107">Member</span></span>                       | <span data-ttu-id="7705a-108">Description</span><span class="sxs-lookup"><span data-stu-id="7705a-108">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="7705a-109">Çalışma zamanının, yöntemin belirli bir örneği için kullanılabilir yerel koda sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7705a-109">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="7705a-110">Yöntemin hafif kod üretimi aracılığıyla dinamik olarak oluşturulup oluşturulmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7705a-110">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="7705a-111">Yöntem tablosundaki yuva numarası.</span><span class="sxs-lookup"><span data-stu-id="7705a-111">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="7705a-112">Metodun ilk yerel adresi.</span><span class="sxs-lookup"><span data-stu-id="7705a-112">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="7705a-113">Çalışma zamanı tarafından dahili olarak kullanılan arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7705a-113">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="7705a-114">`MethodDesc`Çalışma zamanında öğesine işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7705a-114">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="7705a-115">Yöntemleri izlemek için çalışma zamanı tarafından dahili olarak kullanılan bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7705a-115">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="7705a-116">Modül bilgileri için çalışma zamanı tarafından dahili olarak kullanılan bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7705a-116">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="7705a-117">Verilen yöntemle ilişkili belirteç.</span><span class="sxs-lookup"><span data-stu-id="7705a-117">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="7705a-118">Çalışma zamanı tarafından dahili olarak kullanılan bir çöp toplama arabelleğinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7705a-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="7705a-119">Çalışma zamanı tarafından dahili olarak kullanılan bir çöp toplama arabelleğinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7705a-119">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="7705a-120">Yöntem dinamik ise, çalışma zamanı bu arabelleği bilgi izleme için dahili olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="7705a-120">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="7705a-121">Yerel kod adresi verildiğinde istek başına yapıyı doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7705a-121">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="7705a-122">Metodun en son belgelenmiş sürümü hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="7705a-122">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="7705a-123">İstenen yerel adres için ReJIT bilgileri.</span><span class="sxs-lookup"><span data-stu-id="7705a-123">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="7705a-124">Metodun izleme aracılığıyla yeniden derlenen sayısı.</span><span class="sxs-lookup"><span data-stu-id="7705a-124">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="7705a-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7705a-125">Remarks</span></span>

<span data-ttu-id="7705a-126">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="7705a-126">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="7705a-127">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7705a-127">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="7705a-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7705a-128">Requirements</span></span>

<span data-ttu-id="7705a-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7705a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7705a-130">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="7705a-130">**Header:** None</span></span>  
<span data-ttu-id="7705a-131">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="7705a-131">**Library:** None</span></span>  
<span data-ttu-id="7705a-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7705a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7705a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7705a-133">See also</span></span>

- [<span data-ttu-id="7705a-134">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7705a-134">Debugging</span></span>](index.md)
- [<span data-ttu-id="7705a-135">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="7705a-135">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="7705a-136">Ortak Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="7705a-136">Common Data Types</span></span>](../common-data-types-unmanaged-api-reference.md)
