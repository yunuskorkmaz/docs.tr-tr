---
description: 'Daha fazla bilgi edinin: IXCLRDataProcess:: EnumModule yöntemi'
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
ms.openlocfilehash: 33b15da6939a0fb78a4eeafcf75e1a2b2f0d0ab1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800688"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="11528-103">IXCLRDataProcess:: EnumModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="11528-103">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="11528-104">Bu işlemin modüllerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="11528-104">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="11528-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11528-105">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="11528-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11528-106">Parameters</span></span>

`handle`\
<span data-ttu-id="11528-107">[in, out] Modülleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="11528-107">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="11528-108">dışı Numaralandırılmış modül.</span><span class="sxs-lookup"><span data-stu-id="11528-108">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="11528-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11528-109">Remarks</span></span>

<span data-ttu-id="11528-110">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 25th yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="11528-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="11528-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11528-111">Requirements</span></span>

<span data-ttu-id="11528-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11528-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="11528-113">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="11528-113">**Header:** None</span></span>  
<span data-ttu-id="11528-114">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="11528-114">**Library:** None</span></span>  
<span data-ttu-id="11528-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="11528-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="11528-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11528-116">See also</span></span>

- [<span data-ttu-id="11528-117">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="11528-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="11528-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="11528-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="11528-119">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11528-119">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="11528-120">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11528-120">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
