---
title: IXCLRDataMethodDefinition::EnumInstance yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0fbb246f8c4bf791dd705aedf8eab6ef8bfeae56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680276"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="be823-102">IXCLRDataMethodDefinition::EnumInstance yöntemi</span><span class="sxs-lookup"><span data-stu-id="be823-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="be823-103">Bu yöntem tanımını örneklerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="be823-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="be823-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be823-104">Syntax</span></span>

```
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

### <a name="parameters"></a><span data-ttu-id="be823-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be823-105">Parameters</span></span>

<span data-ttu-id="be823-106">`handle` [out içinde] Örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="be823-106">`handle` [in, out] A handle for enumerating the instances.</span></span>

<span data-ttu-id="be823-107">`instance` [out] Numaralandırılmış örneği.</span><span class="sxs-lookup"><span data-stu-id="be823-107">`instance` [out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="be823-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be823-108">Remarks</span></span>

<span data-ttu-id="be823-109">Sağlanan yöntem parçasıdır `IXCLRDataMethodDefinition` arabirim ve sanal yöntem tablosunun dördüncü yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="be823-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="be823-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be823-110">Requirements</span></span>

<span data-ttu-id="be823-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be823-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="be823-112">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="be823-112">**Header:** None</span></span>  
<span data-ttu-id="be823-113">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="be823-113">**Library:** None</span></span>  
<span data-ttu-id="be823-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="be823-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="be823-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be823-115">See also</span></span>

- [<span data-ttu-id="be823-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="be823-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="be823-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="be823-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="be823-118">IXCLRDataMethodDefinition arabirimi</span><span class="sxs-lookup"><span data-stu-id="be823-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="be823-119">IXCLRDataMethodInstance arabirimi</span><span class="sxs-lookup"><span data-stu-id="be823-119">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
