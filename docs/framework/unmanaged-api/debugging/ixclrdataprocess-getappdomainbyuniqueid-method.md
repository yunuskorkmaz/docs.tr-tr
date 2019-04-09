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
ms.openlocfilehash: 257fa2cf03a62ea888b76519aa5c9f9e84038045
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126509"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="3678b-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span><span class="sxs-lookup"><span data-stu-id="3678b-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="3678b-103">Alır bir `AppDomain` bir işlemde kendi benzersiz tanımlayıcısına göre.</span><span class="sxs-lookup"><span data-stu-id="3678b-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3678b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3678b-104">Syntax</span></span>
```
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="3678b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3678b-105">Parameters</span></span>

`id`\
<span data-ttu-id="3678b-106">[in] AppDomain benzersiz tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="3678b-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="3678b-107">[out] Uygulama etki alanı</span><span class="sxs-lookup"><span data-stu-id="3678b-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="3678b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3678b-108">Remarks</span></span>

<span data-ttu-id="3678b-109">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 20 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3678b-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="3678b-110">`IXCLRDataAppDomain*` Döndürülen diğer API'ler ile etkileşim için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3678b-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="3678b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3678b-111">Requirements</span></span>
<span data-ttu-id="3678b-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3678b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="3678b-113">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="3678b-113">**Header:** None</span></span>  
<span data-ttu-id="3678b-114">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="3678b-114">**Library:** None</span></span>  
**<span data-ttu-id="3678b-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="3678b-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="3678b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3678b-116">See also</span></span>

- [<span data-ttu-id="3678b-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3678b-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="3678b-118">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3678b-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
