---
title: IXCLRDataMethodInstance::GetILAddressMap yöntemi
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
ms.openlocfilehash: 66e4768acff7ab735c6ac9e8f8f51a9511f7e371
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744687"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="843a7-102">IXCLRDataMethodInstance::GetILAddressMap yöntemi</span><span class="sxs-lookup"><span data-stu-id="843a7-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="843a7-103">IL adresi eşleme bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="843a7-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="843a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="843a7-104">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="843a7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="843a7-105">Parameters</span></span>

`mapLen`\
<span data-ttu-id="843a7-106">[in] Sağlanan haritalar dizinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="843a7-106">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="843a7-107">[out] Gereken yöntemini eşleme girişleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="843a7-107">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="843a7-108">[out, size_is(mapLen)] Eşleme girişleri depolamak için dizi.</span><span class="sxs-lookup"><span data-stu-id="843a7-108">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="843a7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="843a7-109">Remarks</span></span>

<span data-ttu-id="843a7-110">Sağlanan yöntem parçasıdır `IXCLRDataMethodInstance` arabirim ve sanal yöntem tablosunu 14 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="843a7-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="843a7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="843a7-111">Requirements</span></span>

<span data-ttu-id="843a7-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="843a7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="843a7-113">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="843a7-113">**Header:** None</span></span>  
<span data-ttu-id="843a7-114">**Kitaplığı:** None</span><span class="sxs-lookup"><span data-stu-id="843a7-114">**Library:** None</span></span>  
<span data-ttu-id="843a7-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="843a7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="843a7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="843a7-116">See also</span></span>

- [<span data-ttu-id="843a7-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="843a7-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="843a7-118">IXCLRDataMethodInstance arabirimi</span><span class="sxs-lookup"><span data-stu-id="843a7-118">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
