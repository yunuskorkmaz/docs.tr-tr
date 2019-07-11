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
ms.openlocfilehash: 40ab90a3218d4309cda709004a191e9440fe505d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769574"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="1cc0c-102">IXCLRDataProcess::EnumModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="1cc0c-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="1cc0c-103">Bu işlemin modülleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="1cc0c-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1cc0c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1cc0c-104">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="1cc0c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1cc0c-105">Parameters</span></span>

`handle`\
<span data-ttu-id="1cc0c-106">[out içinde] Modülleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="1cc0c-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="1cc0c-107">[out] Numaralandırılmış modülü.</span><span class="sxs-lookup"><span data-stu-id="1cc0c-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="1cc0c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1cc0c-108">Remarks</span></span>

<span data-ttu-id="1cc0c-109">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve 25 sanal yöntem tablosunu yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1cc0c-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1cc0c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1cc0c-110">Requirements</span></span>

<span data-ttu-id="1cc0c-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cc0c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1cc0c-112">**Üst bilgi:** None</span><span class="sxs-lookup"><span data-stu-id="1cc0c-112">**Header:** None</span></span>  
<span data-ttu-id="1cc0c-113">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="1cc0c-113">**Library:** None</span></span>  
<span data-ttu-id="1cc0c-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1cc0c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1cc0c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cc0c-115">See also</span></span>

- [<span data-ttu-id="1cc0c-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1cc0c-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="1cc0c-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1cc0c-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="1cc0c-118">IXCLRDataModule arabirimi</span><span class="sxs-lookup"><span data-stu-id="1cc0c-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="1cc0c-119">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="1cc0c-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
