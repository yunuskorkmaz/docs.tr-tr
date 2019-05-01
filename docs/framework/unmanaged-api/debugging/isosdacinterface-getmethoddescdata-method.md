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
ms.openlocfilehash: 4e32facc65162c4deb853cd507a00126e5f786e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914881"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="9f30a-102">ISOSDacInterface::GetMethodDescData yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f30a-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="9f30a-103">Verileri için belirli MethodDesc işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="9f30a-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9f30a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f30a-104">Syntax</span></span>

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="9f30a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f30a-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="9f30a-106">[in] MethodDesc adresi.</span><span class="sxs-lookup"><span data-stu-id="9f30a-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="9f30a-107">[in] Yöntem IP adresi.</span><span class="sxs-lookup"><span data-stu-id="9f30a-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="9f30a-108">[out] İç API'lerinden döndürülen MethodDesc ile ilişkili veriler.</span><span class="sxs-lookup"><span data-stu-id="9f30a-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="9f30a-109">[out] Geri döndürülen rejit sürüm sayısı.</span><span class="sxs-lookup"><span data-stu-id="9f30a-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="9f30a-110">[out] İç API'lerinden döndürülen şekilde geri döndürülen rejit sürümleriyle ilişkili veriler.</span><span class="sxs-lookup"><span data-stu-id="9f30a-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="9f30a-111">[out] Geri döndürülen ReJit sürümleriyle ilişkili verileri depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="9f30a-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f30a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f30a-112">Remarks</span></span>

<span data-ttu-id="9f30a-113">Sağlanan yöntem parçasıdır `ISOSDacInterface` arabirim ve sanal yöntem tablosunu 20 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="9f30a-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="9f30a-114">Kullanmaya devam edebilmek için [ `CLRDATA_ADDRESS` ](../common-data-types-unmanaged-api-reference.md) 64-bit işaretsiz tamsayı tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f30a-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f30a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f30a-115">Requirements</span></span>

<span data-ttu-id="9f30a-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f30a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9f30a-117">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="9f30a-117">**Header:** None</span></span>  
<span data-ttu-id="9f30a-118">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="9f30a-118">**Library:** None</span></span>  
<span data-ttu-id="9f30a-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9f30a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9f30a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f30a-120">See also</span></span>

- [<span data-ttu-id="9f30a-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9f30a-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="9f30a-122">ISOSDacInterface arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f30a-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)