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
ms.openlocfilehash: 50ad55674360d7b880af3ddf701cf17005f30ce7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722744"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="f770c-102">IXCLRDataProcess::EndEnumModules yöntemi</span><span class="sxs-lookup"><span data-stu-id="f770c-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="f770c-103">Modül numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="f770c-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f770c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f770c-104">Syntax</span></span>
```
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="f770c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f770c-105">Parameters</span></span>
<span data-ttu-id="f770c-106">`handle` [out] Modülleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="f770c-106">`handle` [out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="f770c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f770c-107">Remarks</span></span>

<span data-ttu-id="f770c-108">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 26 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f770c-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f770c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f770c-109">Requirements</span></span>

<span data-ttu-id="f770c-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f770c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="f770c-111">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f770c-111">**Header:** None</span></span>   
<span data-ttu-id="f770c-112">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f770c-112">**Library:** None</span></span>   
<span data-ttu-id="f770c-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f770c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   

## <a name="see-also"></a><span data-ttu-id="f770c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f770c-114">See also</span></span>

- [<span data-ttu-id="f770c-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f770c-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="f770c-116">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="f770c-116">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
