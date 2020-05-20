---
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
ms.openlocfilehash: d546cda5c68732e75550a3de286089f7df261c91
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420909"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="a06ed-102">IXCLRDataMethodInstance:: GetRepresentativeEntryAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="a06ed-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="a06ed-103">Bir yöntem için tüm olası giriş noktalarının yerel derlenmesi için en temsili giriş noktası adresini alır.</span><span class="sxs-lookup"><span data-stu-id="a06ed-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a06ed-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a06ed-104">Syntax</span></span>

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="a06ed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a06ed-105">Parameters</span></span>

`addr`\
<span data-ttu-id="a06ed-106">dışı Yöntemi için en temsili yerel giriş noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="a06ed-106">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="a06ed-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a06ed-107">Remarks</span></span>

<span data-ttu-id="a06ed-108">Belirtilen yöntem [ `IXCLRDataMethodInstance` arabirimin](ixclrdatamethodinstance-interface.md) bir parçasıdır ve sanal yöntem tablosunun 20. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a06ed-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 20th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a06ed-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a06ed-109">Requirements</span></span>

<span data-ttu-id="a06ed-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a06ed-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a06ed-111">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="a06ed-111">**Header:** None</span></span>  
<span data-ttu-id="a06ed-112">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="a06ed-112">**Library:** None</span></span>  
<span data-ttu-id="a06ed-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a06ed-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a06ed-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a06ed-114">See also</span></span>

- [<span data-ttu-id="a06ed-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a06ed-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="a06ed-116">IXCLRDataMethodInstance Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a06ed-116">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
