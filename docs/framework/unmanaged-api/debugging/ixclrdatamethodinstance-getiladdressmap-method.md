---
title: 'IXCLRDataMethodInstance:: Getıladdressmap yöntemi'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0acfa9ffd6f4bc3be567855008dccd08c9c74153
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420922"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="34f6b-102">IXCLRDataMethodInstance:: Getıladdressmap yöntemi</span><span class="sxs-lookup"><span data-stu-id="34f6b-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="34f6b-103">Eşleme bilgilerini ele almak için Il 'yi alır.</span><span class="sxs-lookup"><span data-stu-id="34f6b-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="34f6b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="34f6b-104">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="34f6b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34f6b-105">Parameters</span></span>

`mapLen`\
<span data-ttu-id="34f6b-106">'ndaki Belirtilen haritalar dizisinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="34f6b-106">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="34f6b-107">dışı Metodun ihtiyacı olan eşleme girdilerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="34f6b-107">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="34f6b-108">[Out, size_is (mapLen)] Harita girdilerini depolamak için dizi.</span><span class="sxs-lookup"><span data-stu-id="34f6b-108">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="34f6b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34f6b-109">Remarks</span></span>

<span data-ttu-id="34f6b-110">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataMethodInstance` ve sanal yöntem tablosunun 15. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="34f6b-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 15th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="34f6b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34f6b-111">Requirements</span></span>

<span data-ttu-id="34f6b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34f6b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="34f6b-113">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="34f6b-113">**Header:** None</span></span>  
<span data-ttu-id="34f6b-114">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="34f6b-114">**Library:** None</span></span>  
<span data-ttu-id="34f6b-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="34f6b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="34f6b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34f6b-116">See also</span></span>

- [<span data-ttu-id="34f6b-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="34f6b-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="34f6b-118">IXCLRDataMethodInstance Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34f6b-118">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
