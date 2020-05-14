---
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
ms.openlocfilehash: 72560de9777b2d826418e63b4a4fcccf1e4fa8b9
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396476"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="b4080-102">IXCLRDataMethodDefinition:: Enumınstance yöntemi</span><span class="sxs-lookup"><span data-stu-id="b4080-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="b4080-103">Bu yöntem tanımının örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="b4080-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b4080-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4080-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="b4080-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4080-105">Parameters</span></span>

`handle`\
<span data-ttu-id="b4080-106">[in, out] Örnekleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="b4080-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="b4080-107">dışı Numaralandırılmış örnek.</span><span class="sxs-lookup"><span data-stu-id="b4080-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4080-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4080-108">Remarks</span></span>

<span data-ttu-id="b4080-109">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataMethodDefinition` ve sanal yöntem tablosunun 6 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b4080-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 6th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b4080-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4080-110">Requirements</span></span>

<span data-ttu-id="b4080-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4080-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b4080-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="b4080-112">**Header:** None</span></span>  
<span data-ttu-id="b4080-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="b4080-113">**Library:** None</span></span>  
<span data-ttu-id="b4080-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b4080-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b4080-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4080-115">See also</span></span>

- [<span data-ttu-id="b4080-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b4080-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="b4080-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b4080-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="b4080-118">IXCLRDataMethodDefinition Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4080-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="b4080-119">IXCLRDataMethodInstance Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4080-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
