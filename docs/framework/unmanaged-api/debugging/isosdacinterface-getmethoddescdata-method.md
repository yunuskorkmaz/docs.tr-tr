---
title: 'Iosdacınterface:: GetMethodDescData yöntemi'
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 105149d0abf312c33a8498e7428e3a8b23d6ae7d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421026"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="c5268-102">Iosdacınterface:: GetMethodDescData yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5268-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="c5268-103">Verilen MethodDesc işaretçisi için verileri alır.</span><span class="sxs-lookup"><span data-stu-id="c5268-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c5268-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c5268-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="c5268-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5268-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="c5268-106">'ndaki MethodDesc adresi.</span><span class="sxs-lookup"><span data-stu-id="c5268-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="c5268-107">'ndaki Metodun IP adresi.</span><span class="sxs-lookup"><span data-stu-id="c5268-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="c5268-108">dışı İç API 'lerden döndürülen MethodDesc ile ilişkili veriler.</span><span class="sxs-lookup"><span data-stu-id="c5268-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="c5268-109">dışı Geri döndürülen yeniden JIT sürümü sayısı.</span><span class="sxs-lookup"><span data-stu-id="c5268-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="c5268-110">dışı İç API 'lerden döndürülen geri döndürülen yeniden JIT sürümleriyle ilişkili veriler.</span><span class="sxs-lookup"><span data-stu-id="c5268-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="c5268-111">dışı Geri döndürülen ReJIT sürümleriyle ilişkili verileri depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="c5268-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5268-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5268-112">Remarks</span></span>

<span data-ttu-id="c5268-113">Belirtilen yöntem arabirimin bir parçasıdır `ISOSDacInterface` ve sanal yöntem tablosunun 21 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="c5268-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 21st slot of the virtual method table.</span></span> <span data-ttu-id="c5268-114">Bunları kullanabilmeniz için, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) 64 bitlik işaretsiz bir tamsayı olarak tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5268-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="c5268-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5268-115">Requirements</span></span>

<span data-ttu-id="c5268-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5268-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c5268-117">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="c5268-117">**Header:** None</span></span>  
<span data-ttu-id="c5268-118">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="c5268-118">**Library:** None</span></span>  
<span data-ttu-id="c5268-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c5268-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c5268-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5268-120">See also</span></span>

- [<span data-ttu-id="c5268-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c5268-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="c5268-122">ISOSDacInterface Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5268-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
