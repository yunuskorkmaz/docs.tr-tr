---
title: IXCLRDataProcess::StartEnumMethodInstancesByAddress yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 88ce9dd928871d71058fe28c243a9fb51b729778
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416205"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="c5ec7-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5ec7-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="c5ec7-103">Yöntem örneklerini listelemek için bir tanıtıcı sağlar `AppDomain` belirli bir adreste başlayan.</span><span class="sxs-lookup"><span data-stu-id="c5ec7-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c5ec7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5ec7-104">Syntax</span></span>

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

### <a name="parameters"></a><span data-ttu-id="c5ec7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5ec7-105">Parameters</span></span>

<span data-ttu-id="c5ec7-106">`address` [in] İlk yöntem örneği adresi.</span><span class="sxs-lookup"><span data-stu-id="c5ec7-106">`address` [in] The address of the first method instance.</span></span>

<span data-ttu-id="c5ec7-107">`appDomain` [in] AppDomain yöntemi örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c5ec7-107">`appDomain` [in] The AppDomain of the method instances.</span></span>

<span data-ttu-id="c5ec7-108">`handle` [out] Yöntem örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="c5ec7-108">`handle` [out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5ec7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5ec7-109">Remarks</span></span>

<span data-ttu-id="c5ec7-110">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 27 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="c5ec7-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 27th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="c5ec7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5ec7-111">Requirements</span></span>

<span data-ttu-id="c5ec7-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5ec7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c5ec7-113">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="c5ec7-113">**Header:** None</span></span>  
<span data-ttu-id="c5ec7-114">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="c5ec7-114">**Library:** None</span></span>  
<span data-ttu-id="c5ec7-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c5ec7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c5ec7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5ec7-116">See Also</span></span>

- [<span data-ttu-id="c5ec7-117">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c5ec7-117">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="c5ec7-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c5ec7-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="c5ec7-119">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5ec7-119">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
