---
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
ms.openlocfilehash: 9a7a23e53f5c2bc7d643046830cf335fec780f11
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420844"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="cb64c-102">IXCLRDataProcess:: EndEnumModules yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb64c-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="cb64c-103">Modül numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="cb64c-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="cb64c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cb64c-104">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="cb64c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb64c-105">Parameters</span></span>

`handle`\
<span data-ttu-id="cb64c-106">dışı Modülleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="cb64c-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb64c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb64c-107">Remarks</span></span>

<span data-ttu-id="cb64c-108">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 26. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="cb64c-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb64c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb64c-109">Requirements</span></span>

<span data-ttu-id="cb64c-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb64c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="cb64c-111">**Üst bilgi:** Hiçbiri **Kitaplığı:** hiçbiri **.NET Framework sürümler:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cb64c-111">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cb64c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb64c-112">See also</span></span>

- [<span data-ttu-id="cb64c-113">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cb64c-113">Debugging</span></span>](index.md)
- [<span data-ttu-id="cb64c-114">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb64c-114">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
