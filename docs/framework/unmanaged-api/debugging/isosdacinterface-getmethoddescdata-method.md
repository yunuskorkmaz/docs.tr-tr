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
ms.openlocfilehash: e4c44379d9db0f5e98f3ca66ec0486961ec2df3a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396941"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="e983f-102">Iosdacınterface:: GetMethodDescData yöntemi</span><span class="sxs-lookup"><span data-stu-id="e983f-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="e983f-103">Verilen MethodDesc işaretçisi için verileri alır.</span><span class="sxs-lookup"><span data-stu-id="e983f-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e983f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e983f-104">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="e983f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e983f-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="e983f-106">'ndaki MethodDesc adresi.</span><span class="sxs-lookup"><span data-stu-id="e983f-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="e983f-107">'ndaki Metodun IP adresi.</span><span class="sxs-lookup"><span data-stu-id="e983f-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="e983f-108">dışı İç API 'lerden döndürülen MethodDesc ile ilişkili veriler.</span><span class="sxs-lookup"><span data-stu-id="e983f-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="e983f-109">dışı Geri döndürülen yeniden JIT sürümü sayısı.</span><span class="sxs-lookup"><span data-stu-id="e983f-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="e983f-110">dışı İç API 'lerden döndürülen geri döndürülen yeniden JIT sürümleriyle ilişkili veriler.</span><span class="sxs-lookup"><span data-stu-id="e983f-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="e983f-111">dışı Geri döndürülen ReJIT sürümleriyle ilişkili verileri depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="e983f-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="e983f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e983f-112">Remarks</span></span>

<span data-ttu-id="e983f-113">Belirtilen yöntem arabirimin bir parçasıdır `ISOSDacInterface` ve sanal yöntem tablosunun 21 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e983f-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 21st slot of the virtual method table.</span></span> <span data-ttu-id="e983f-114">Bunları kullanabilmeniz için, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) 64 bitlik işaretsiz bir tamsayı olarak tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e983f-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="e983f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e983f-115">Requirements</span></span>

<span data-ttu-id="e983f-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e983f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e983f-117">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="e983f-117">**Header:** None</span></span>  
<span data-ttu-id="e983f-118">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="e983f-118">**Library:** None</span></span>  
<span data-ttu-id="e983f-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e983f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e983f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e983f-120">See also</span></span>

- [<span data-ttu-id="e983f-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e983f-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="e983f-122">ISOSDacInterface Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e983f-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
