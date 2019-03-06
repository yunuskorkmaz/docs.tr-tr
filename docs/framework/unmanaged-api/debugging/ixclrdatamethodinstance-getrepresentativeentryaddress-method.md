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
ms.openlocfilehash: 6f204e2ed9cb1409d53432355467bb11946f8809
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372457"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="ba71a-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba71a-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="ba71a-103">Bir yöntem için tüm olası girdi noktalarını native derlemesi için en iyi temsil giriş noktası adresi alır.</span><span class="sxs-lookup"><span data-stu-id="ba71a-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ba71a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba71a-104">Syntax</span></span>

```
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="ba71a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba71a-105">Parameters</span></span>

`addr`\
<span data-ttu-id="ba71a-106">[out] Yöntemi için en iyi temsil yerel giriş noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="ba71a-106">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba71a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba71a-107">Remarks</span></span>

<span data-ttu-id="ba71a-108">Sağlanan yöntem parçasıdır [ `IXCLRDataMethodInstance` arabirimi](ixclrdatamethodinstance-interface.md) ve sanal yöntem tablo 19 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="ba71a-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 19th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba71a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba71a-109">Requirements</span></span>

<span data-ttu-id="ba71a-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba71a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ba71a-111">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ba71a-111">**Header:** None</span></span>  
<span data-ttu-id="ba71a-112">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ba71a-112">**Library:** None</span></span>  
<span data-ttu-id="ba71a-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ba71a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ba71a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba71a-114">See also</span></span>

- [<span data-ttu-id="ba71a-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ba71a-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="ba71a-116">IXCLRDataMethodInstance arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba71a-116">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
