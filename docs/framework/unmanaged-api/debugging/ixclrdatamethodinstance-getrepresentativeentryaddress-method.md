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
ms.openlocfilehash: d9f9e16d243c0f3b45ac24776caea5bb9c32dcc1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395746"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="0dee7-102">IXCLRDataMethodInstance:: GetRepresentativeEntryAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="0dee7-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="0dee7-103">Bir yöntem için tüm olası giriş noktalarının yerel derlenmesi için en temsili giriş noktası adresini alır.</span><span class="sxs-lookup"><span data-stu-id="0dee7-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0dee7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0dee7-104">Syntax</span></span>

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="0dee7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0dee7-105">Parameters</span></span>

`addr`\
<span data-ttu-id="0dee7-106">dışı Yöntemi için en temsili yerel giriş noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="0dee7-106">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="0dee7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0dee7-107">Remarks</span></span>

<span data-ttu-id="0dee7-108">Belirtilen yöntem [ `IXCLRDataMethodInstance` arabirimin](ixclrdatamethodinstance-interface.md) bir parçasıdır ve sanal yöntem tablosunun 20. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="0dee7-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 20th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0dee7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0dee7-109">Requirements</span></span>

<span data-ttu-id="0dee7-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dee7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0dee7-111">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="0dee7-111">**Header:** None</span></span>  
<span data-ttu-id="0dee7-112">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="0dee7-112">**Library:** None</span></span>  
<span data-ttu-id="0dee7-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0dee7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0dee7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dee7-114">See also</span></span>

- [<span data-ttu-id="0dee7-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0dee7-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="0dee7-116">IXCLRDataMethodInstance Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dee7-116">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
