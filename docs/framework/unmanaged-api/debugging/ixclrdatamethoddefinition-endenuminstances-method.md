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
ms.openlocfilehash: 7271c9594a679af205c404f59ff6731821aa0acf
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421000"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="c4d00-102">IXCLRDataMethodDefinition:: Endenumınstances yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4d00-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="c4d00-103">Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="c4d00-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c4d00-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c4d00-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="c4d00-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4d00-105">Parameters</span></span>

`handle`\
<span data-ttu-id="c4d00-106">dışı Örnekleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="c4d00-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4d00-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4d00-107">Remarks</span></span>

<span data-ttu-id="c4d00-108">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataMethodDefinition` ve sanal yöntem tablosunun 7. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="c4d00-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 7th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="c4d00-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4d00-109">Requirements</span></span>

<span data-ttu-id="c4d00-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4d00-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c4d00-111">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="c4d00-111">**Header:** None</span></span>  
<span data-ttu-id="c4d00-112">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="c4d00-112">**Library:** None</span></span>  
<span data-ttu-id="c4d00-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c4d00-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c4d00-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4d00-114">See also</span></span>

- [<span data-ttu-id="c4d00-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c4d00-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="c4d00-116">IXCLRDataMethodDefinition Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4d00-116">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
