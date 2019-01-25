---
title: IXCLRDataMethodDefinition::EndEnumInstances yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4a7cd8850778e9bbbc7d8d67f464c7787e40bc13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566105"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="ecd3d-102">IXCLRDataMethodDefinition::EndEnumInstances yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecd3d-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="ecd3d-103">Örnek numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="ecd3d-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ecd3d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecd3d-104">Syntax</span></span>

```
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="ecd3d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ecd3d-105">Parameters</span></span>

<span data-ttu-id="ecd3d-106">`handle` [out] Örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="ecd3d-106">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="ecd3d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecd3d-107">Remarks</span></span>

<span data-ttu-id="ecd3d-108">Sağlanan yöntem parçasıdır `IXCLRDataMethodDefinition` arabirim ve sanal yöntem tablosunu beşinci yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="ecd3d-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ecd3d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecd3d-109">Requirements</span></span>

<span data-ttu-id="ecd3d-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecd3d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ecd3d-111">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ecd3d-111">**Header:** None</span></span>  
<span data-ttu-id="ecd3d-112">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ecd3d-112">**Library:** None</span></span>  
<span data-ttu-id="ecd3d-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ecd3d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ecd3d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecd3d-114">See also</span></span>

- [<span data-ttu-id="ecd3d-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ecd3d-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="ecd3d-116">IXCLRDataMethodDefinition arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd3d-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
