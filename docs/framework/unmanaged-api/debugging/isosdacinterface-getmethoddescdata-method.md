---
title: ISOSDacInterface::GetMethodDescData yöntemi
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
ms.openlocfilehash: 3f22752446413c622a20340541b0ac328f63c77b
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416214"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="9a071-102">ISOSDacInterface::GetMethodDescData yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a071-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="9a071-103">Verileri alır verilen [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="9a071-103">Gets the data for the given [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9a071-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a071-104">Syntax</span></span>

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    void                       *data,
    ULONG                      cRevertedRejitVersions,
    void                      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a><span data-ttu-id="9a071-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a071-105">Parameters</span></span>

<span data-ttu-id="9a071-106">`methodDesc` [in] MethodDesc adresi.</span><span class="sxs-lookup"><span data-stu-id="9a071-106">`methodDesc` [in] The address of the MethodDesc.</span></span>

<span data-ttu-id="9a071-107">`ip` [in] Yöntem IP adresi.</span><span class="sxs-lookup"><span data-stu-id="9a071-107">`ip` [in] The IP address of the method.</span></span>

<span data-ttu-id="9a071-108">`data` [out] İç API'lerinden döndürülen MethodDesc ile ilişkili veriler.</span><span class="sxs-lookup"><span data-stu-id="9a071-108">`data` [out] The data associated with the MethodDesc as returned from the internal APIs.</span></span> <span data-ttu-id="9a071-109">Yapısı en az 168 bayt gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a071-109">The structure needs at least 168 bytes.</span></span>

<span data-ttu-id="9a071-110">`cRevertedRejitVersions` [out] Geri döndürülen rejit sürüm sayısı.</span><span class="sxs-lookup"><span data-stu-id="9a071-110">`cRevertedRejitVersions` [out] The number of reverted rejit versions.</span></span>

<span data-ttu-id="9a071-111">`rgRevertedRejitData` [out] İç API'lerinden döndürülen şekilde geri döndürülen rejit sürümleriyle ilişkili veriler.</span><span class="sxs-lookup"><span data-stu-id="9a071-111">`rgRevertedRejitData` [out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span> <span data-ttu-id="9a071-112">Yapısı en az 24 bayt gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a071-112">The structure needs at least 24 bytes.</span></span>

<span data-ttu-id="9a071-113">`pcNeededRevertedRejitData` [out] Geri döndürülen ReJit sürümleriyle ilişkili verileri depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="9a071-113">`pcNeededRevertedRejitData` [out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a071-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a071-114">Remarks</span></span>

<span data-ttu-id="9a071-115">Sağlanan yöntem parçasıdır `ISOSDacInterface` arabirim ve sanal yöntem tablosunu 20 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="9a071-115">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="9a071-116">Ayrıca `CLRDATA_ADDRESS` 64-bit işaretsiz tamsayı olan.</span><span class="sxs-lookup"><span data-stu-id="9a071-116">Also the `CLRDATA_ADDRESS` are 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="9a071-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a071-117">Requirements</span></span>

<span data-ttu-id="9a071-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a071-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9a071-119">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9a071-119">**Header:** None</span></span>  
<span data-ttu-id="9a071-120">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9a071-120">**Library:** None</span></span>  
<span data-ttu-id="9a071-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9a071-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9a071-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a071-122">See Also</span></span>

- [<span data-ttu-id="9a071-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9a071-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="9a071-124">ISOSDacInterface arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a071-124">ISOSDacInterface Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
