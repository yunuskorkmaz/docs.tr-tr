---
title: IXCLRDataProcess::EnumModule yöntemi
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
ms.openlocfilehash: 1648e53df5f36f7615831b425d2b5d764731c5c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738137"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="21742-102">IXCLRDataProcess::EnumModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="21742-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="21742-103">Bu işlemin modülleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="21742-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="21742-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21742-104">Syntax</span></span>

```
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

### <a name="parameters"></a><span data-ttu-id="21742-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21742-105">Parameters</span></span>

<span data-ttu-id="21742-106">`handle` [out içinde] Modülleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="21742-106">`handle` [in, out] A handle for enumerating the modules.</span></span>

<span data-ttu-id="21742-107">`mod` [out] Numaralandırılmış modülü.</span><span class="sxs-lookup"><span data-stu-id="21742-107">`mod` [out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="21742-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21742-108">Remarks</span></span>

<span data-ttu-id="21742-109">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve 25 sanal yöntem tablosunu yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="21742-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="21742-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21742-110">Requirements</span></span>

<span data-ttu-id="21742-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21742-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="21742-112">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="21742-112">**Header:** None</span></span>  
<span data-ttu-id="21742-113">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="21742-113">**Library:** None</span></span>  
<span data-ttu-id="21742-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="21742-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="21742-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21742-115">See also</span></span>

- [<span data-ttu-id="21742-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="21742-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="21742-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="21742-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="21742-118">IXCLRDataModule arabirimi</span><span class="sxs-lookup"><span data-stu-id="21742-118">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
- [<span data-ttu-id="21742-119">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="21742-119">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
