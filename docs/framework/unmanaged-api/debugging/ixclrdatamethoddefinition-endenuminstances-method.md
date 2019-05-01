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
ms.openlocfilehash: 28cd15a793d303e1d6e64c52c1d0095e8d619c7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789707"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="12755-102">IXCLRDataMethodDefinition::EndEnumInstances yöntemi</span><span class="sxs-lookup"><span data-stu-id="12755-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="12755-103">Örnek numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="12755-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="12755-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12755-104">Syntax</span></span>

```
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="12755-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12755-105">Parameters</span></span>

`handle`\
<span data-ttu-id="12755-106">[out] Örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="12755-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="12755-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12755-107">Remarks</span></span>

<span data-ttu-id="12755-108">Sağlanan yöntem parçasıdır `IXCLRDataMethodDefinition` arabirim ve sanal yöntem tablosunu beşinci yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="12755-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="12755-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12755-109">Requirements</span></span>

<span data-ttu-id="12755-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12755-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="12755-111">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="12755-111">**Header:** None</span></span>  
<span data-ttu-id="12755-112">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="12755-112">**Library:** None</span></span>  
<span data-ttu-id="12755-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="12755-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="12755-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12755-114">See also</span></span>

- [<span data-ttu-id="12755-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="12755-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="12755-116">IXCLRDataMethodDefinition arabirimi</span><span class="sxs-lookup"><span data-stu-id="12755-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
