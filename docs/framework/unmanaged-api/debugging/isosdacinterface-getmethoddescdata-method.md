---
description: 'Şu konuda daha fazla bilgi edinin: ısosdacınterface:: GetMethodDescData yöntemi'
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
ms.openlocfilehash: a1284aa4d810ed9d6db7ad3c1b471702b1dad54d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790431"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="d0fdd-103">Iosdacınterface:: GetMethodDescData yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0fdd-103">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="d0fdd-104">Verilen MethodDesc işaretçisi için verileri alır.</span><span class="sxs-lookup"><span data-stu-id="d0fdd-104">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d0fdd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0fdd-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="d0fdd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0fdd-106">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="d0fdd-107">'ndaki MethodDesc adresi.</span><span class="sxs-lookup"><span data-stu-id="d0fdd-107">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="d0fdd-108">'ndaki Metodun IP adresi.</span><span class="sxs-lookup"><span data-stu-id="d0fdd-108">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="d0fdd-109">dışı İç API 'lerden döndürülen MethodDesc ile ilişkili veriler.</span><span class="sxs-lookup"><span data-stu-id="d0fdd-109">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="d0fdd-110">dışı Geri döndürülen yeniden JIT sürümü sayısı.</span><span class="sxs-lookup"><span data-stu-id="d0fdd-110">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="d0fdd-111">dışı İç API 'lerden döndürülen geri döndürülen yeniden JIT sürümleriyle ilişkili veriler.</span><span class="sxs-lookup"><span data-stu-id="d0fdd-111">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="d0fdd-112">dışı Geri döndürülen ReJIT sürümleriyle ilişkili verileri depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="d0fdd-112">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0fdd-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0fdd-113">Remarks</span></span>

<span data-ttu-id="d0fdd-114">Belirtilen yöntem arabirimin bir parçasıdır `ISOSDacInterface` ve sanal yöntem tablosunun 21 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d0fdd-114">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 21st slot of the virtual method table.</span></span> <span data-ttu-id="d0fdd-115">Bunları kullanabilmeniz için, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) 64 bitlik işaretsiz bir tamsayı olarak tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0fdd-115">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0fdd-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0fdd-116">Requirements</span></span>

<span data-ttu-id="d0fdd-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0fdd-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d0fdd-118">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="d0fdd-118">**Header:** None</span></span>  
<span data-ttu-id="d0fdd-119">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="d0fdd-119">**Library:** None</span></span>  
<span data-ttu-id="d0fdd-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d0fdd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d0fdd-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0fdd-121">See also</span></span>

- [<span data-ttu-id="d0fdd-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d0fdd-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="d0fdd-123">ISOSDacInterface Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0fdd-123">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
