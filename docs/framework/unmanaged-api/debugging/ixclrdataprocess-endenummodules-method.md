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
ms.openlocfilehash: 3b7050e92af6fc58b45837840b2796a5deac955c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375343"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="92058-102">IXCLRDataProcess::EndEnumModules yöntemi</span><span class="sxs-lookup"><span data-stu-id="92058-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="92058-103">Modül numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="92058-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="92058-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92058-104">Syntax</span></span>
```
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="92058-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92058-105">Parameters</span></span>

`handle`\
<span data-ttu-id="92058-106">[out] Modülleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="92058-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="92058-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92058-107">Remarks</span></span>

<span data-ttu-id="92058-108">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 26 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="92058-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="92058-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92058-109">Requirements</span></span>

<span data-ttu-id="92058-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92058-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="92058-111">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="92058-111">**Header:** None</span></span>   
<span data-ttu-id="92058-112">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="92058-112">**Library:** None</span></span>   
<span data-ttu-id="92058-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="92058-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   

## <a name="see-also"></a><span data-ttu-id="92058-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92058-114">See also</span></span>

- [<span data-ttu-id="92058-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="92058-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="92058-116">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="92058-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
