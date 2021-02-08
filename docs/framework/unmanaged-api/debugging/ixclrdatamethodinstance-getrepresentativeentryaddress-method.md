---
description: 'Daha fazla bilgi edinin: IXCLRDataMethodInstance:: GetRepresentativeEntryAddress yöntemi'
title: 'IXCLRDataMethodInstance:: GetRepresentativeEntryAddress yöntemi'
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 21cc6c50ab460c0e3a3a92c11fcfe51d4a2a4606
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800805"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="e1f18-103">IXCLRDataMethodInstance:: GetRepresentativeEntryAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1f18-103">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="e1f18-104">Bir yöntem için tüm olası giriş noktalarının yerel derlenmesi için en temsili giriş noktası adresini alır.</span><span class="sxs-lookup"><span data-stu-id="e1f18-104">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e1f18-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1f18-105">Syntax</span></span>

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="e1f18-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1f18-106">Parameters</span></span>

`addr`\
<span data-ttu-id="e1f18-107">dışı Yöntemi için en temsili yerel giriş noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="e1f18-107">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1f18-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1f18-108">Remarks</span></span>

<span data-ttu-id="e1f18-109">Belirtilen yöntem [ `IXCLRDataMethodInstance` arabirimin](ixclrdatamethodinstance-interface.md) bir parçasıdır ve sanal yöntem tablosunun 20. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e1f18-109">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 20th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e1f18-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1f18-110">Requirements</span></span>

<span data-ttu-id="e1f18-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1f18-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e1f18-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="e1f18-112">**Header:** None</span></span>  
<span data-ttu-id="e1f18-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="e1f18-113">**Library:** None</span></span>  
<span data-ttu-id="e1f18-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e1f18-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e1f18-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1f18-115">See also</span></span>

- [<span data-ttu-id="e1f18-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e1f18-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="e1f18-117">IXCLRDataMethodInstance Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1f18-117">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
