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
ms.openlocfilehash: b6393d7fa4853c230203521e665bbe89d7b228e2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790438"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="7aeda-102">IXCLRDataMethodDefinition:: Enumınstance yöntemi</span><span class="sxs-lookup"><span data-stu-id="7aeda-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="7aeda-103">Bu yöntem tanımının örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7aeda-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7aeda-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7aeda-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="7aeda-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7aeda-105">Parameters</span></span>

`handle`\
<span data-ttu-id="7aeda-106">[in, out] Örnekleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="7aeda-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="7aeda-107">dışı Numaralandırılmış örnek.</span><span class="sxs-lookup"><span data-stu-id="7aeda-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="7aeda-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7aeda-108">Remarks</span></span>

<span data-ttu-id="7aeda-109">Belirtilen yöntem `IXCLRDataMethodDefinition` arabiriminin bir parçasıdır ve sanal yöntem tablosunun dördüncü yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="7aeda-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7aeda-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7aeda-110">Requirements</span></span>

<span data-ttu-id="7aeda-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aeda-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7aeda-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="7aeda-112">**Header:** None</span></span>  
<span data-ttu-id="7aeda-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="7aeda-113">**Library:** None</span></span>  
<span data-ttu-id="7aeda-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7aeda-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7aeda-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7aeda-115">See also</span></span>

- [<span data-ttu-id="7aeda-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7aeda-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="7aeda-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7aeda-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="7aeda-118">IXCLRDataMethodDefinition arabirimi</span><span class="sxs-lookup"><span data-stu-id="7aeda-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="7aeda-119">IXCLRDataMethodInstance arabirimi</span><span class="sxs-lookup"><span data-stu-id="7aeda-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
