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
ms.openlocfilehash: 8442d1373ede241d262ab41928fd5d9924ec9c80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567197"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="2d037-102">IXCLRDataMethodInstance::GetILAddressMap yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d037-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="2d037-103">IL adresi eşleme bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="2d037-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2d037-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d037-104">Syntax</span></span>

```
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

### <a name="parameters"></a><span data-ttu-id="2d037-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d037-105">Parameters</span></span>

<span data-ttu-id="2d037-106">`mapLen` [in] Sağlanan haritalar dizinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="2d037-106">`mapLen` [in] The length of the provided maps array.</span></span>

<span data-ttu-id="2d037-107">`mapNeeded` [out] Gereken yöntemini eşleme girişleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="2d037-107">`mapNeeded` [out] The number of map entries that the method needs.</span></span>

<span data-ttu-id="2d037-108">`maps` [out, size_is(mapLen)] Eşleme girişleri depolamak için dizi.</span><span class="sxs-lookup"><span data-stu-id="2d037-108">`maps` [out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d037-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d037-109">Remarks</span></span>

<span data-ttu-id="2d037-110">Sağlanan yöntem parçasıdır `IXCLRDataMethodInstance` arabirim ve sanal yöntem tablosunu 14 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="2d037-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d037-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d037-111">Requirements</span></span>

<span data-ttu-id="2d037-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d037-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2d037-113">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="2d037-113">**Header:** None</span></span>  
<span data-ttu-id="2d037-114">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="2d037-114">**Library:** None</span></span>  
<span data-ttu-id="2d037-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2d037-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2d037-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d037-116">See also</span></span>

- [<span data-ttu-id="2d037-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2d037-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="2d037-118">IXCLRDataMethodInstance arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d037-118">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
