---
title: 'IXCLRDataModule:: GetMethodDefinitionByToken yöntemi'
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
ms.openlocfilehash: 074949145be588fc34266a9f2ee501caeeffb9d3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420883"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="74c27-102">IXCLRDataModule:: GetMethodDefinitionByToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="74c27-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="74c27-103">Belirtilen meta veri belirtecine karşılık gelen yöntem tanımını alır.</span><span class="sxs-lookup"><span data-stu-id="74c27-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="74c27-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="74c27-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="74c27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74c27-105">Parameters</span></span>

`token`\
<span data-ttu-id="74c27-106">'ndaki Yöntem belirteci.</span><span class="sxs-lookup"><span data-stu-id="74c27-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="74c27-107">dışı Yöntem tanımı.</span><span class="sxs-lookup"><span data-stu-id="74c27-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="74c27-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74c27-108">Remarks</span></span>

<span data-ttu-id="74c27-109">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataModule` ve sanal yöntem tablosunun 26. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="74c27-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="74c27-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74c27-110">Requirements</span></span>

<span data-ttu-id="74c27-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74c27-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="74c27-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="74c27-112">**Header:** None</span></span>  
<span data-ttu-id="74c27-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="74c27-113">**Library:** None</span></span>  
<span data-ttu-id="74c27-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="74c27-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="74c27-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74c27-115">See also</span></span>

- [<span data-ttu-id="74c27-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="74c27-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="74c27-117">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74c27-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
