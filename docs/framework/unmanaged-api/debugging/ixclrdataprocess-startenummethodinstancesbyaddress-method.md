---
title: IXCLRDataProcess::StartEnumMethodInstancesByAddress yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 8d0494e53705493de814ed4d4caa869e1e8a700f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374576"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="c56a9-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="c56a9-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="c56a9-103">Yöntem örneklerini listelemek için bir tanıtıcı sağlar `AppDomain` belirli bir adreste başlayan.</span><span class="sxs-lookup"><span data-stu-id="c56a9-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c56a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c56a9-104">Syntax</span></span>

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

### <a name="parameters"></a><span data-ttu-id="c56a9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c56a9-105">Parameters</span></span>

`address`\
<span data-ttu-id="c56a9-106">[in] İlk yöntem örneği adresi.</span><span class="sxs-lookup"><span data-stu-id="c56a9-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="c56a9-107">[in] AppDomain yöntemi örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c56a9-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="c56a9-108">[out] Yöntem örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="c56a9-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="c56a9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c56a9-109">Remarks</span></span>

<span data-ttu-id="c56a9-110">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 27 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="c56a9-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 27th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="c56a9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c56a9-111">Requirements</span></span>

<span data-ttu-id="c56a9-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c56a9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c56a9-113">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="c56a9-113">**Header:** None</span></span>  
<span data-ttu-id="c56a9-114">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="c56a9-114">**Library:** None</span></span>  
<span data-ttu-id="c56a9-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c56a9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c56a9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c56a9-116">See also</span></span>

- [<span data-ttu-id="c56a9-117">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c56a9-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="c56a9-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c56a9-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="c56a9-119">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="c56a9-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
