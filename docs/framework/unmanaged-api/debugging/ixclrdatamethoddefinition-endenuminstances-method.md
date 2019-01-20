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
ms.openlocfilehash: 7901ba3ac95052e265df619d06996b4c9ce8baa6
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416138"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="c29f9-102">IXCLRDataMethodDefinition::EndEnumInstances yöntemi</span><span class="sxs-lookup"><span data-stu-id="c29f9-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="c29f9-103">Örnek numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="c29f9-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c29f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c29f9-104">Syntax</span></span>

```
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="c29f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c29f9-105">Parameters</span></span>

<span data-ttu-id="c29f9-106">`handle` [out] Örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="c29f9-106">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="c29f9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c29f9-107">Remarks</span></span>

<span data-ttu-id="c29f9-108">Sağlanan yöntem parçasıdır `IXCLRDataMethodDefinition` arabirim ve sanal yöntem tablosunu beşinci yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="c29f9-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="c29f9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c29f9-109">Requirements</span></span>

<span data-ttu-id="c29f9-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c29f9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c29f9-111">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="c29f9-111">**Header:** None</span></span>  
<span data-ttu-id="c29f9-112">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="c29f9-112">**Library:** None</span></span>  
<span data-ttu-id="c29f9-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c29f9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c29f9-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c29f9-114">See Also</span></span>

- [<span data-ttu-id="c29f9-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c29f9-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="c29f9-116">IXCLRDataMethodDefinition arabirimi</span><span class="sxs-lookup"><span data-stu-id="c29f9-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
