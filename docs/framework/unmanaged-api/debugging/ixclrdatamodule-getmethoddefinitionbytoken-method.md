---
title: IXCLRDataModule::GetMethodDefinitionByToken yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 27f1ee28aff95340d4b533473b2f699a9405c3a2
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416215"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="d8ac9-102">IXCLRDataModule::GetMethodDefinitionByToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8ac9-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="d8ac9-103">Belirli bir metaveri belirteci için karşılık gelen yöntem tanımını alır.</span><span class="sxs-lookup"><span data-stu-id="d8ac9-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d8ac9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8ac9-104">Syntax</span></span>

```
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

### <a name="parameters"></a><span data-ttu-id="d8ac9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8ac9-105">Parameters</span></span>

<span data-ttu-id="d8ac9-106">`token` [in] Token metody</span><span class="sxs-lookup"><span data-stu-id="d8ac9-106">`token` [in] The method token.</span></span>

<span data-ttu-id="d8ac9-107">`methodDefinition` [out] Yöntem tanımı.</span><span class="sxs-lookup"><span data-stu-id="d8ac9-107">`methodDefinition` [out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8ac9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8ac9-108">Remarks</span></span>

<span data-ttu-id="d8ac9-109">Sağlanan yöntem parçasıdır `IXCLRDataModule` arabirim ve 25 sanal yöntem tablosunu yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d8ac9-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8ac9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8ac9-110">Requirements</span></span>

<span data-ttu-id="d8ac9-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ac9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d8ac9-112">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="d8ac9-112">**Header:** None</span></span>  
<span data-ttu-id="d8ac9-113">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="d8ac9-113">**Library:** None</span></span>  
<span data-ttu-id="d8ac9-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ac9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="d8ac9-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8ac9-115">See Also</span></span>

- [<span data-ttu-id="d8ac9-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d8ac9-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="d8ac9-117">IXCLRDataModule arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8ac9-117">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
