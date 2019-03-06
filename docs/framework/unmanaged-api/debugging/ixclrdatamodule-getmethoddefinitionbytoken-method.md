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
ms.openlocfilehash: 727005437289b4bc66ab90f280b80a79f4db06db
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359321"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="0f305-102">IXCLRDataModule::GetMethodDefinitionByToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f305-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="0f305-103">Belirli bir metaveri belirteci için karşılık gelen yöntem tanımını alır.</span><span class="sxs-lookup"><span data-stu-id="0f305-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0f305-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f305-104">Syntax</span></span>

```
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="0f305-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f305-105">Parameters</span></span>

`token`\
<span data-ttu-id="0f305-106">[in] Token metody</span><span class="sxs-lookup"><span data-stu-id="0f305-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="0f305-107">[out] Yöntem tanımı.</span><span class="sxs-lookup"><span data-stu-id="0f305-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f305-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f305-108">Remarks</span></span>

<span data-ttu-id="0f305-109">Sağlanan yöntem parçasıdır `IXCLRDataModule` arabirim ve 25 sanal yöntem tablosunu yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="0f305-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f305-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f305-110">Requirements</span></span>

<span data-ttu-id="0f305-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f305-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0f305-112">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="0f305-112">**Header:** None</span></span>  
<span data-ttu-id="0f305-113">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="0f305-113">**Library:** None</span></span>  
<span data-ttu-id="0f305-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0f305-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="0f305-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f305-115">See also</span></span>

- [<span data-ttu-id="0f305-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0f305-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="0f305-117">IXCLRDataModule arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f305-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
