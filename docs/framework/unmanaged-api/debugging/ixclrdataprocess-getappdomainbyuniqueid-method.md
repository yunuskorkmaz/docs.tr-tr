---
title: IXCLRDataProcess::GetAppDomainByUniqueId Method
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 83e7d4e1a4ff3c2e6f573d6c097c7cdb9c5f3c54
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416207"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="9e0d4-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span><span class="sxs-lookup"><span data-stu-id="9e0d4-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="9e0d4-103">Alır bir `AppDomain` bir işlemde kendi benzersiz tanımlayıcısına göre.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9e0d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e0d4-104">Syntax</span></span>
```
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

### <a name="parameters"></a><span data-ttu-id="9e0d4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e0d4-105">Parameters</span></span>
<span data-ttu-id="9e0d4-106">`id` [in] AppDomain benzersiz tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="9e0d4-106">`id` [in] The unique identifier of the AppDomain</span></span>

<span data-ttu-id="9e0d4-107">`appDomain` [out] Uygulama etki alanı</span><span class="sxs-lookup"><span data-stu-id="9e0d4-107">`appDomain` [out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="9e0d4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e0d4-108">Remarks</span></span>

<span data-ttu-id="9e0d4-109">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 20 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="9e0d4-110">`IXCLRDataAppDomain*` Döndürülen diğer API'ler ile etkileşim için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e0d4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e0d4-111">Requirements</span></span>
<span data-ttu-id="9e0d4-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e0d4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9e0d4-113">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9e0d4-113">**Header:** None</span></span>  
<span data-ttu-id="9e0d4-114">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9e0d4-114">**Library:** None</span></span>  
<span data-ttu-id="9e0d4-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9e0d4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9e0d4-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-116">See Also</span></span>
- [<span data-ttu-id="9e0d4-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9e0d4-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="9e0d4-118">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e0d4-118">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
