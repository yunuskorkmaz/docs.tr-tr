---
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
ms.openlocfilehash: d623fe862eaf5902fd89d0e512dd07f73a03246f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860811"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="1be1f-102">DacpMethodDescData Yapısı</span><span class="sxs-lookup"><span data-stu-id="1be1f-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="1be1f-103">Metodun çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1be1f-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1be1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1be1f-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="1be1f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1be1f-105">Members</span></span>

| <span data-ttu-id="1be1f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1be1f-106">Member</span></span>                       | <span data-ttu-id="1be1f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1be1f-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="1be1f-108">Çalışma zamanının, yöntemin belirli bir örneği için kullanılabilir yerel koda sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1be1f-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="1be1f-109">Yöntemin hafif kod üretimi aracılığıyla dinamik olarak oluşturulup oluşturulmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1be1f-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="1be1f-110">Yöntem tablosundaki yuva numarası.</span><span class="sxs-lookup"><span data-stu-id="1be1f-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="1be1f-111">Metodun ilk yerel adresi.</span><span class="sxs-lookup"><span data-stu-id="1be1f-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="1be1f-112">Çalışma zamanı tarafından dahili olarak kullanılan arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1be1f-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="1be1f-113">Çalışma zamanında öğesine `MethodDesc` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1be1f-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="1be1f-114">Yöntemleri izlemek için çalışma zamanı tarafından dahili olarak kullanılan bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1be1f-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="1be1f-115">Modül bilgileri için çalışma zamanı tarafından dahili olarak kullanılan bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1be1f-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="1be1f-116">Verilen yöntemle ilişkili belirteç.</span><span class="sxs-lookup"><span data-stu-id="1be1f-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="1be1f-117">Çalışma zamanı tarafından dahili olarak kullanılan bir çöp toplama arabelleğinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1be1f-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="1be1f-118">Çalışma zamanı tarafından dahili olarak kullanılan bir çöp toplama arabelleğinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1be1f-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="1be1f-119">Yöntem dinamik ise, çalışma zamanı bu arabelleği bilgi izleme için dahili olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="1be1f-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="1be1f-120">Yerel kod adresi verildiğinde istek başına yapıyı doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1be1f-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="1be1f-121">Metodun en son belgelenmiş sürümü hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="1be1f-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="1be1f-122">İstenen yerel adres için ReJIT bilgileri.</span><span class="sxs-lookup"><span data-stu-id="1be1f-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="1be1f-123">Metodun izleme aracılığıyla yeniden derlenen sayısı.</span><span class="sxs-lookup"><span data-stu-id="1be1f-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="1be1f-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1be1f-124">Remarks</span></span>

<span data-ttu-id="1be1f-125">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="1be1f-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="1be1f-126">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1be1f-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="1be1f-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1be1f-127">Requirements</span></span>
<span data-ttu-id="1be1f-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1be1f-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1be1f-129">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1be1f-129">**Header:** None</span></span>  
<span data-ttu-id="1be1f-130">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1be1f-130">**Library:** None</span></span>  
<span data-ttu-id="1be1f-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1be1f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1be1f-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1be1f-132">See also</span></span>

- [<span data-ttu-id="1be1f-133">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1be1f-133">Debugging</span></span>](index.md)
- [<span data-ttu-id="1be1f-134">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="1be1f-134">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="1be1f-135">Ortak Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="1be1f-135">Common Data Types</span></span>](../common-data-types-unmanaged-api-reference.md)
