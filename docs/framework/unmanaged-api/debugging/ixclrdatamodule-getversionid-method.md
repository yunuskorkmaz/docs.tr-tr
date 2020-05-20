---
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
ms.openlocfilehash: 9d5ef137a5d76c3d7545ab16921352123e978fb1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420870"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="7e4fc-102">IXCLRDataModule:: Getversionıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e4fc-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="7e4fc-103">Modülün sürüm tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="7e4fc-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7e4fc-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7e4fc-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="7e4fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e4fc-105">Parameters</span></span>

`vid`\
<span data-ttu-id="7e4fc-106">dışı Modülün sürüm tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7e4fc-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e4fc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e4fc-107">Remarks</span></span>

<span data-ttu-id="7e4fc-108">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataModule` ve sanal yöntem tablosunun 41 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="7e4fc-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e4fc-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e4fc-109">Requirements</span></span>

<span data-ttu-id="7e4fc-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e4fc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7e4fc-111">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="7e4fc-111">**Header:** None</span></span>  
<span data-ttu-id="7e4fc-112">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="7e4fc-112">**Library:** None</span></span>  
<span data-ttu-id="7e4fc-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7e4fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7e4fc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e4fc-114">See also</span></span>

- [<span data-ttu-id="7e4fc-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7e4fc-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="7e4fc-116">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e4fc-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
