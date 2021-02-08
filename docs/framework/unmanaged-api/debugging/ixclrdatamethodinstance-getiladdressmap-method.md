---
description: ': IXCLRDataMethodInstance:: Getıladdressmap yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ddddf593c3c18f2b4cd1682b5d6f7c8ff1985ac6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800818"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="ee2ba-103">IXCLRDataMethodInstance:: Getıladdressmap yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee2ba-103">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="ee2ba-104">Eşleme bilgilerini ele almak için Il 'yi alır.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-104">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ee2ba-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee2ba-105">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="ee2ba-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee2ba-106">Parameters</span></span>

`mapLen`\
<span data-ttu-id="ee2ba-107">'ndaki Belirtilen haritalar dizisinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-107">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="ee2ba-108">dışı Metodun ihtiyacı olan eşleme girdilerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-108">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="ee2ba-109">[Out, size_is (mapLen)] Harita girdilerini depolamak için dizi.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-109">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee2ba-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee2ba-110">Remarks</span></span>

<span data-ttu-id="ee2ba-111">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataMethodInstance` ve sanal yöntem tablosunun 15. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-111">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 15th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee2ba-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee2ba-112">Requirements</span></span>

<span data-ttu-id="ee2ba-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee2ba-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ee2ba-114">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="ee2ba-114">**Header:** None</span></span>  
<span data-ttu-id="ee2ba-115">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="ee2ba-115">**Library:** None</span></span>  
<span data-ttu-id="ee2ba-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ee2ba-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ee2ba-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee2ba-117">See also</span></span>

- [<span data-ttu-id="ee2ba-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ee2ba-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="ee2ba-119">IXCLRDataMethodInstance Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee2ba-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
