---
title: 'IXCLRDataProcess:: EnumModule yöntemi'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5caadcfe091393a8ff79106d57a50a532c349829
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420787"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="9b648-102">IXCLRDataProcess:: EnumModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b648-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="9b648-103">Bu işlemin modüllerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="9b648-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9b648-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9b648-104">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="9b648-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b648-105">Parameters</span></span>

`handle`\
<span data-ttu-id="9b648-106">[in, out] Modülleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="9b648-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="9b648-107">dışı Numaralandırılmış modül.</span><span class="sxs-lookup"><span data-stu-id="9b648-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b648-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b648-108">Remarks</span></span>

<span data-ttu-id="9b648-109">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 25th yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="9b648-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="9b648-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b648-110">Requirements</span></span>

<span data-ttu-id="9b648-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b648-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9b648-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="9b648-112">**Header:** None</span></span>  
<span data-ttu-id="9b648-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="9b648-113">**Library:** None</span></span>  
<span data-ttu-id="9b648-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9b648-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9b648-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b648-115">See also</span></span>

- [<span data-ttu-id="9b648-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9b648-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="9b648-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9b648-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="9b648-118">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b648-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="9b648-119">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b648-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
