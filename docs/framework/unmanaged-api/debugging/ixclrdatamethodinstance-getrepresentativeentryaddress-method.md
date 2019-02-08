---
title: IXCLRDataMethodInstance::GetRepresentativeEntryAddress yöntemi
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
ms.openlocfilehash: 52b2fdaaefd16a49300641f44041b8352141385b
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828559"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="3e551-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e551-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="3e551-103">Bir yöntem için tüm olası girdi noktalarını native derlemesi için en iyi temsil giriş noktası adresi alır.</span><span class="sxs-lookup"><span data-stu-id="3e551-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3e551-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e551-104">Syntax</span></span>

```
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

### <a name="parameters"></a><span data-ttu-id="3e551-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e551-105">Parameters</span></span>

<span data-ttu-id="3e551-106">`addr` [out] Yöntemi için en iyi temsil yerel giriş noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="3e551-106">`addr` [out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e551-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e551-107">Remarks</span></span>

<span data-ttu-id="3e551-108">Sağlanan yöntem parçasıdır [ `IXCLRDataMethodInstance` arabirimi](ixclrdatamethodinstance-interface.md) ve sanal yöntem tablo 19 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3e551-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 19th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e551-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e551-109">Requirements</span></span>

<span data-ttu-id="3e551-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e551-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3e551-111">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="3e551-111">**Header:** None</span></span>  
<span data-ttu-id="3e551-112">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="3e551-112">**Library:** None</span></span>  
<span data-ttu-id="3e551-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3e551-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3e551-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e551-114">See also</span></span>

- [<span data-ttu-id="3e551-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3e551-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="3e551-116">IXCLRDataMethodInstance arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e551-116">IXCLRDataMethodInstance Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
