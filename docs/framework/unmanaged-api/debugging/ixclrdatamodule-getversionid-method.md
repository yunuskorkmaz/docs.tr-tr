---
description: 'Şu konuda daha fazla bilgi edinin: IXCLRDataModule:: Getversionıd yöntemi'
title: 'IXCLRDataModule:: Getversionıd yöntemi'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1b924757f43d106df555ea028270ac873f8f4558
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800766"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="aca2d-103">IXCLRDataModule:: Getversionıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="aca2d-103">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="aca2d-104">Modülün sürüm tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="aca2d-104">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="aca2d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aca2d-105">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="aca2d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aca2d-106">Parameters</span></span>

`vid`\
<span data-ttu-id="aca2d-107">dışı Modülün sürüm tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="aca2d-107">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="aca2d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aca2d-108">Remarks</span></span>

<span data-ttu-id="aca2d-109">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataModule` ve sanal yöntem tablosunun 41 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="aca2d-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="aca2d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aca2d-110">Requirements</span></span>

<span data-ttu-id="aca2d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aca2d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="aca2d-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="aca2d-112">**Header:** None</span></span>  
<span data-ttu-id="aca2d-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="aca2d-113">**Library:** None</span></span>  
<span data-ttu-id="aca2d-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aca2d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="aca2d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aca2d-115">See also</span></span>

- [<span data-ttu-id="aca2d-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="aca2d-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="aca2d-117">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aca2d-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
