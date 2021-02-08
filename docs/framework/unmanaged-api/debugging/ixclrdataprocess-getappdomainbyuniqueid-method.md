---
description: ': IXCLRDataProcess:: Getappdomainbyuniqueıd yöntemi hakkında daha fazla bilgi edinin'
title: 'IXCLRDataProcess:: Getappdomainbyuniqueıd yöntemi'
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
ms.openlocfilehash: 7087362efbb810fcb6e1b6f7eb9f23c54c38fade
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800675"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="7633b-103">IXCLRDataProcess:: Getappdomainbyuniqueıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="7633b-103">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="7633b-104">`AppDomain`Benzersiz tanımlayıcısına göre bir işlem içinde alır.</span><span class="sxs-lookup"><span data-stu-id="7633b-104">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7633b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7633b-105">Syntax</span></span>

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="7633b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7633b-106">Parameters</span></span>

`id`\
<span data-ttu-id="7633b-107">'ndaki AppDomain 'in benzersiz tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="7633b-107">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="7633b-108">dışı AppDomain</span><span class="sxs-lookup"><span data-stu-id="7633b-108">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="7633b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7633b-109">Remarks</span></span>

<span data-ttu-id="7633b-110">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 20. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="7633b-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="7633b-111">`IXCLRDataAppDomain*`Döndürülen diğer API 'lerle etkileşim için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7633b-111">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="7633b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7633b-112">Requirements</span></span>

<span data-ttu-id="7633b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7633b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="7633b-114">**Üst bilgi:** Hiçbiri **Kitaplığı:** hiçbiri **.NET Framework sürümler:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7633b-114">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7633b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7633b-115">See also</span></span>

- [<span data-ttu-id="7633b-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7633b-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="7633b-117">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7633b-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
