---
title: IXCLRDataProcess::EndEnumModules yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: cd49ae5fa274c577cfa3c04ec599e488384dfc64
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416199"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="5ef8d-102">IXCLRDataProcess::EndEnumModules yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ef8d-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="5ef8d-103">Modül numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="5ef8d-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5ef8d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ef8d-104">Syntax</span></span>
```
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="5ef8d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ef8d-105">Parameters</span></span>
<span data-ttu-id="5ef8d-106">`handle` [out] Modülleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="5ef8d-106">`handle` [out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ef8d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ef8d-107">Remarks</span></span>

<span data-ttu-id="5ef8d-108">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 26 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="5ef8d-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ef8d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ef8d-109">Requirements</span></span>

<span data-ttu-id="5ef8d-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ef8d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="5ef8d-111">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="5ef8d-111">**Header:** None</span></span>   
<span data-ttu-id="5ef8d-112">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="5ef8d-112">**Library:** None</span></span>   
<span data-ttu-id="5ef8d-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5ef8d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   

## <a name="see-also"></a><span data-ttu-id="5ef8d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ef8d-114">See Also</span></span>

- [<span data-ttu-id="5ef8d-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5ef8d-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="5ef8d-116">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ef8d-116">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
