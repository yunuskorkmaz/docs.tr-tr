---
description: 'Daha fazla bilgi edinin: IXCLRDataProcess:: EndEnumModules yöntemi'
title: 'IXCLRDataProcess:: EndEnumModules yöntemi'
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
ms.openlocfilehash: 454d4fa3616f9ba8312dc3d1ac02c228625aa488
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800714"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="5ec22-103">IXCLRDataProcess:: EndEnumModules yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ec22-103">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="5ec22-104">Modül numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="5ec22-104">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5ec22-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ec22-105">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="5ec22-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ec22-106">Parameters</span></span>

`handle`\
<span data-ttu-id="5ec22-107">dışı Modülleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="5ec22-107">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ec22-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ec22-108">Remarks</span></span>

<span data-ttu-id="5ec22-109">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 26. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="5ec22-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ec22-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ec22-110">Requirements</span></span>

<span data-ttu-id="5ec22-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ec22-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="5ec22-112">**Üst bilgi:** Hiçbiri **Kitaplığı:** hiçbiri **.NET Framework sürümler:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5ec22-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5ec22-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ec22-113">See also</span></span>

- [<span data-ttu-id="5ec22-114">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5ec22-114">Debugging</span></span>](index.md)
- [<span data-ttu-id="5ec22-115">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ec22-115">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
