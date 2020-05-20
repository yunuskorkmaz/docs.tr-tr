---
title: 'IXCLRDataProcess:: StartEnumModules yöntemi'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d55b07ea3fada73237919bf677163a9096d5ad04
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420727"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="588a1-102">IXCLRDataProcess:: StartEnumModules yöntemi</span><span class="sxs-lookup"><span data-stu-id="588a1-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="588a1-103">Bir işlemin modüllerini numaralandırmak için bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="588a1-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="588a1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="588a1-104">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="588a1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="588a1-105">Parameters</span></span>

`handle`\
<span data-ttu-id="588a1-106">dışı Modülleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="588a1-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="588a1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="588a1-107">Remarks</span></span>

<span data-ttu-id="588a1-108">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 24. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="588a1-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="588a1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="588a1-109">Requirements</span></span>

<span data-ttu-id="588a1-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="588a1-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="588a1-111">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="588a1-111">**Header:** None</span></span>  
<span data-ttu-id="588a1-112">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="588a1-112">**Library:** None</span></span>  
<span data-ttu-id="588a1-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="588a1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="588a1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="588a1-114">See also</span></span>

- [<span data-ttu-id="588a1-115">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="588a1-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="588a1-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="588a1-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="588a1-117">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="588a1-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
