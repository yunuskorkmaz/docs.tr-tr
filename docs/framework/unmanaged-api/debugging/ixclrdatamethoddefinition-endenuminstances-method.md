---
title: 'IXCLRDataMethodDefinition:: Endenumınstances yöntemi'
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
ms.openlocfilehash: 605a4244d20ef6c0b7af3c2b26b65ff2a63fa9dd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790454"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="16460-102">IXCLRDataMethodDefinition:: Endenumınstances yöntemi</span><span class="sxs-lookup"><span data-stu-id="16460-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="16460-103">Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="16460-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="16460-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16460-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="16460-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16460-105">Parameters</span></span>

`handle`\
<span data-ttu-id="16460-106">dışı Örnekleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="16460-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="16460-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16460-107">Remarks</span></span>

<span data-ttu-id="16460-108">Belirtilen yöntem `IXCLRDataMethodDefinition` arabiriminin bir parçasıdır ve sanal yöntem tablosunun beşinci yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="16460-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="16460-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16460-109">Requirements</span></span>

<span data-ttu-id="16460-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16460-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="16460-111">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="16460-111">**Header:** None</span></span>  
<span data-ttu-id="16460-112">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="16460-112">**Library:** None</span></span>  
<span data-ttu-id="16460-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="16460-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="16460-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16460-114">See also</span></span>

- [<span data-ttu-id="16460-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="16460-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="16460-116">IXCLRDataMethodDefinition arabirimi</span><span class="sxs-lookup"><span data-stu-id="16460-116">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
