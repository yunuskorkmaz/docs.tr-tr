---
description: 'Daha fazla bilgi edinin: IXCLRDataMethodDefinition:: Enumınstance yöntemi'
title: 'IXCLRDataMethodDefinition:: Enumınstance yöntemi'
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
ms.openlocfilehash: 4038dc4706b8362acaf9c13abd9c7326cce376a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790366"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="bce97-103">IXCLRDataMethodDefinition:: Enumınstance yöntemi</span><span class="sxs-lookup"><span data-stu-id="bce97-103">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="bce97-104">Bu yöntem tanımının örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="bce97-104">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bce97-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bce97-105">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="bce97-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bce97-106">Parameters</span></span>

`handle`\
<span data-ttu-id="bce97-107">[in, out] Örnekleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="bce97-107">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="bce97-108">dışı Numaralandırılmış örnek.</span><span class="sxs-lookup"><span data-stu-id="bce97-108">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="bce97-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bce97-109">Remarks</span></span>

<span data-ttu-id="bce97-110">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataMethodDefinition` ve sanal yöntem tablosunun 6 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="bce97-110">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 6th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="bce97-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bce97-111">Requirements</span></span>

<span data-ttu-id="bce97-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bce97-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="bce97-113">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="bce97-113">**Header:** None</span></span>  
<span data-ttu-id="bce97-114">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="bce97-114">**Library:** None</span></span>  
<span data-ttu-id="bce97-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bce97-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bce97-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bce97-116">See also</span></span>

- [<span data-ttu-id="bce97-117">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bce97-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="bce97-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bce97-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="bce97-119">IXCLRDataMethodDefinition Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bce97-119">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="bce97-120">IXCLRDataMethodInstance Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bce97-120">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
