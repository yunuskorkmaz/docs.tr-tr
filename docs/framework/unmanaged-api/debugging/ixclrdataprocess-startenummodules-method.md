---
description: 'Şu konuda daha fazla bilgi edinin: IXCLRDataProcess:: StartEnumModules yöntemi'
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
ms.openlocfilehash: 2e90c646ee8815ec10ce0bbd7538f13d7b5dcf8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800593"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="1825b-103">IXCLRDataProcess:: StartEnumModules yöntemi</span><span class="sxs-lookup"><span data-stu-id="1825b-103">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="1825b-104">Bir işlemin modüllerini numaralandırmak için bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1825b-104">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1825b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1825b-105">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="1825b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1825b-106">Parameters</span></span>

`handle`\
<span data-ttu-id="1825b-107">dışı Modülleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="1825b-107">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="1825b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1825b-108">Remarks</span></span>

<span data-ttu-id="1825b-109">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 24. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1825b-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1825b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1825b-110">Requirements</span></span>

<span data-ttu-id="1825b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1825b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1825b-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1825b-112">**Header:** None</span></span>  
<span data-ttu-id="1825b-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1825b-113">**Library:** None</span></span>  
<span data-ttu-id="1825b-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1825b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1825b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1825b-115">See also</span></span>

- [<span data-ttu-id="1825b-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1825b-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="1825b-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1825b-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="1825b-118">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1825b-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
