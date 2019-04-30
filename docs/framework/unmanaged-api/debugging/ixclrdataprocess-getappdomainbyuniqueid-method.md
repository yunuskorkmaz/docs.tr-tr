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
ms.openlocfilehash: 8b468d40ef8eb523ba8881627fae15cf9b7c7b80
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775271"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="05380-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span><span class="sxs-lookup"><span data-stu-id="05380-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="05380-103">Alır bir `AppDomain` bir işlemde kendi benzersiz tanımlayıcısına göre.</span><span class="sxs-lookup"><span data-stu-id="05380-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="05380-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05380-104">Syntax</span></span>

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="05380-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05380-105">Parameters</span></span>

`id`\
<span data-ttu-id="05380-106">[in] AppDomain benzersiz tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="05380-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="05380-107">[out] Uygulama etki alanı</span><span class="sxs-lookup"><span data-stu-id="05380-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="05380-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05380-108">Remarks</span></span>

<span data-ttu-id="05380-109">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 20 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="05380-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="05380-110">`IXCLRDataAppDomain*` Döndürülen diğer API'ler ile etkileşim için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="05380-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="05380-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05380-111">Requirements</span></span>

<span data-ttu-id="05380-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05380-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="05380-113">**Üst bilgi:** Hiçbiri **kitaplığı:** Hiçbiri **.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="05380-113">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="05380-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05380-114">See also</span></span>

- [<span data-ttu-id="05380-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="05380-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="05380-116">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="05380-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
