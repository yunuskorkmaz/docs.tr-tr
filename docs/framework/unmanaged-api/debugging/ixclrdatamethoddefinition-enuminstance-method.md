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
ms.openlocfilehash: dacf76582916ad50f51ae7c8818b496f31f9553e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771936"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="57a8f-102">IXCLRDataMethodDefinition::EnumInstance yöntemi</span><span class="sxs-lookup"><span data-stu-id="57a8f-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="57a8f-103">Bu yöntem tanımını örneklerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="57a8f-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="57a8f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57a8f-104">Syntax</span></span>

```
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="57a8f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57a8f-105">Parameters</span></span>

`handle`\
<span data-ttu-id="57a8f-106">[out içinde] Örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="57a8f-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="57a8f-107">[out] Numaralandırılmış örneği.</span><span class="sxs-lookup"><span data-stu-id="57a8f-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="57a8f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57a8f-108">Remarks</span></span>

<span data-ttu-id="57a8f-109">Sağlanan yöntem parçasıdır `IXCLRDataMethodDefinition` arabirim ve sanal yöntem tablosunun dördüncü yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="57a8f-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="57a8f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57a8f-110">Requirements</span></span>

<span data-ttu-id="57a8f-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57a8f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="57a8f-112">**Üst bilgi:** None</span><span class="sxs-lookup"><span data-stu-id="57a8f-112">**Header:** None</span></span>  
<span data-ttu-id="57a8f-113">**Kitaplığı:** None</span><span class="sxs-lookup"><span data-stu-id="57a8f-113">**Library:** None</span></span>  
<span data-ttu-id="57a8f-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="57a8f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="57a8f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57a8f-115">See also</span></span>

- [<span data-ttu-id="57a8f-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="57a8f-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="57a8f-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="57a8f-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="57a8f-118">IXCLRDataMethodDefinition arabirimi</span><span class="sxs-lookup"><span data-stu-id="57a8f-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="57a8f-119">IXCLRDataMethodInstance arabirimi</span><span class="sxs-lookup"><span data-stu-id="57a8f-119">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
