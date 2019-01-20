---
title: IXCLRDataMethodDefinition::StartEnumInstances yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 208d6c46f18834b23e642efa82df0a365013a410
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416141"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="74c39-102">IXCLRDataMethodDefinition::StartEnumInstances yöntemi</span><span class="sxs-lookup"><span data-stu-id="74c39-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="74c39-103">Numaralandırma yöntemi örnekleri için bir tanıtıcı sağlayan bir verilen `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="74c39-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="74c39-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74c39-104">Syntax</span></span>

```
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

### <a name="parameters"></a><span data-ttu-id="74c39-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74c39-105">Parameters</span></span>

<span data-ttu-id="74c39-106">`appDomain` [in] AppDomain için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="74c39-106">`appDomain` [in] An AppDomain for the enumeration.</span></span>

<span data-ttu-id="74c39-107">`handle` [out] Örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="74c39-107">`handle` [out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="74c39-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74c39-108">Remarks</span></span>

<span data-ttu-id="74c39-109">Sağlanan yöntem parçasıdır `IXCLRDataMethodDefinition` arabirim ve sanal yöntem tablosunu üçüncü yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="74c39-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the third slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="74c39-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74c39-110">Requirements</span></span>

<span data-ttu-id="74c39-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74c39-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="74c39-112">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="74c39-112">**Header:** None</span></span>  
<span data-ttu-id="74c39-113">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="74c39-113">**Library:** None</span></span>  
<span data-ttu-id="74c39-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="74c39-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="74c39-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74c39-115">See Also</span></span>

- [<span data-ttu-id="74c39-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="74c39-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="74c39-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="74c39-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="74c39-118">IXCLRDataMethodDefinition arabirimi</span><span class="sxs-lookup"><span data-stu-id="74c39-118">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
