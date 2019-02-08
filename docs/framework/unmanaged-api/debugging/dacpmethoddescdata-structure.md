---
title: DacpMethodDescData yapısı
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
ms.openlocfilehash: e9037fc035693e079e2471ad37263108656b8c01
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828541"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="f61c6-102">DacpMethodDescData yapısı</span><span class="sxs-lookup"><span data-stu-id="f61c6-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="f61c6-103">Bir yöntemin çalışma zamanı bilgileri için transport arabellek tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f61c6-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f61c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f61c6-104">Syntax</span></span>

```
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

## <a name="members"></a><span data-ttu-id="f61c6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f61c6-105">Members</span></span>

| <span data-ttu-id="f61c6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f61c6-106">Member</span></span>                       | <span data-ttu-id="f61c6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f61c6-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="f61c6-108">Çalışma zamanı yerel kod yöntemin belirli örneklemesi için kullanılabilir olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f61c6-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="f61c6-109">Basit kod oluşturma yöntemini dinamik olarak oluşturulur, gösterir.</span><span class="sxs-lookup"><span data-stu-id="f61c6-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="f61c6-110">Yöntem tablosunu yöntemin yuva numarası.</span><span class="sxs-lookup"><span data-stu-id="f61c6-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="f61c6-111">Yöntemin ilk yerel adres.</span><span class="sxs-lookup"><span data-stu-id="f61c6-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="f61c6-112">Çalışma zamanı tarafından dahili olarak kullanılan arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f61c6-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="f61c6-113">İşaretçi `MethodDesc` çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="f61c6-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="f61c6-114">Dahili yöntemleri izlemek için çalışma zamanı tarafından kullanılan arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f61c6-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="f61c6-115">Çalışma zamanı tarafından modülü bilgileri için dahili olarak kullanılan arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f61c6-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="f61c6-116">Belirtilen yöntemle ilişkili belirteci.</span><span class="sxs-lookup"><span data-stu-id="f61c6-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="f61c6-117">Çalışma zamanı tarafından dahili olarak kullanılan bir çöp toplama arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f61c6-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="f61c6-118">Çalışma zamanı tarafından dahili olarak kullanılan bir çöp toplama arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f61c6-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="f61c6-119">Yöntem dinamik ise, çalışma zamanı bu arabellek izleme bilgileri için dahili olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="f61c6-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="f61c6-120">Yerel kod adresi verildiğinde istek başına yapısı doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f61c6-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="f61c6-121">Yöntemin belgelenmiş en son sürüm hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="f61c6-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="f61c6-122">İstenen yerel adres için Rejit bilgileri.</span><span class="sxs-lookup"><span data-stu-id="f61c6-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="f61c6-123">İzleme aracılığıyla rejitted yöntemi çağrıldıysa sayısı.</span><span class="sxs-lookup"><span data-stu-id="f61c6-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |


## <a name="remarks"></a><span data-ttu-id="f61c6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f61c6-124">Remarks</span></span>

<span data-ttu-id="f61c6-125">Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="f61c6-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="f61c6-126">Bunu kullanmak için yukarıda belirtildiği gibi yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f61c6-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="f61c6-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f61c6-127">Requirements</span></span>
<span data-ttu-id="f61c6-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f61c6-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f61c6-129">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f61c6-129">**Header:** None</span></span>  
<span data-ttu-id="f61c6-130">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f61c6-130">**Library:** None</span></span>  
<span data-ttu-id="f61c6-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f61c6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f61c6-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f61c6-132">See also</span></span>
- [<span data-ttu-id="f61c6-133">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f61c6-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="f61c6-134">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="f61c6-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="f61c6-135">Ortak Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="f61c6-135">Common Data Types</span></span>](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
