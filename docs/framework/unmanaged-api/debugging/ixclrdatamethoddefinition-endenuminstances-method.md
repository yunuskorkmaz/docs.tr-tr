---
description: 'Daha fazla bilgi edinin: IXCLRDataMethodDefinition:: Endenumınstances yöntemi'
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
ms.openlocfilehash: bfdcb9046b4983e6686410bf2ceadf7119b89e74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790379"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="7c44a-103">IXCLRDataMethodDefinition:: Endenumınstances yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c44a-103">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="7c44a-104">Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="7c44a-104">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7c44a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c44a-105">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="7c44a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c44a-106">Parameters</span></span>

`handle`\
<span data-ttu-id="7c44a-107">dışı Örnekleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="7c44a-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c44a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c44a-108">Remarks</span></span>

<span data-ttu-id="7c44a-109">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataMethodDefinition` ve sanal yöntem tablosunun 7. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="7c44a-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 7th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7c44a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c44a-110">Requirements</span></span>

<span data-ttu-id="7c44a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c44a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7c44a-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="7c44a-112">**Header:** None</span></span>  
<span data-ttu-id="7c44a-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="7c44a-113">**Library:** None</span></span>  
<span data-ttu-id="7c44a-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7c44a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7c44a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c44a-115">See also</span></span>

- [<span data-ttu-id="7c44a-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7c44a-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="7c44a-117">IXCLRDataMethodDefinition Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c44a-117">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
