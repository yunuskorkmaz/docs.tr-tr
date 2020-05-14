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
ms.openlocfilehash: 7c4dcf59ce159434d5012120043f5bb548d49731
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396814"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="2ed05-102">IXCLRDataMethodInstance:: Getıladdressmap yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ed05-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="2ed05-103">Eşleme bilgilerini ele almak için Il 'yi alır.</span><span class="sxs-lookup"><span data-stu-id="2ed05-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2ed05-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ed05-104">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="2ed05-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ed05-105">Parameters</span></span>

`mapLen`\
<span data-ttu-id="2ed05-106">'ndaki Belirtilen haritalar dizisinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="2ed05-106">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="2ed05-107">dışı Metodun ihtiyacı olan eşleme girdilerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="2ed05-107">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="2ed05-108">[Out, size_is (mapLen)] Harita girdilerini depolamak için dizi.</span><span class="sxs-lookup"><span data-stu-id="2ed05-108">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ed05-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ed05-109">Remarks</span></span>

<span data-ttu-id="2ed05-110">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataMethodInstance` ve sanal yöntem tablosunun 15. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="2ed05-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 15th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ed05-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ed05-111">Requirements</span></span>

<span data-ttu-id="2ed05-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ed05-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2ed05-113">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="2ed05-113">**Header:** None</span></span>  
<span data-ttu-id="2ed05-114">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="2ed05-114">**Library:** None</span></span>  
<span data-ttu-id="2ed05-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2ed05-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2ed05-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ed05-116">See also</span></span>

- [<span data-ttu-id="2ed05-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2ed05-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="2ed05-118">IXCLRDataMethodInstance Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ed05-118">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
