---
description: 'Şu konuda daha fazla bilgi edinin: IXCLRDataModule:: GetMethodDefinitionByToken yöntemi'
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
ms.openlocfilehash: 1eb1187d09183bfff97324a8032d23cbf471f580
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800779"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="ad409-103">IXCLRDataModule:: GetMethodDefinitionByToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad409-103">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="ad409-104">Belirtilen meta veri belirtecine karşılık gelen yöntem tanımını alır.</span><span class="sxs-lookup"><span data-stu-id="ad409-104">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ad409-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad409-105">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="ad409-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad409-106">Parameters</span></span>

`token`\
<span data-ttu-id="ad409-107">'ndaki Yöntem belirteci.</span><span class="sxs-lookup"><span data-stu-id="ad409-107">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="ad409-108">dışı Yöntem tanımı.</span><span class="sxs-lookup"><span data-stu-id="ad409-108">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad409-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad409-109">Remarks</span></span>

<span data-ttu-id="ad409-110">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataModule` ve sanal yöntem tablosunun 26. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="ad409-110">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ad409-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad409-111">Requirements</span></span>

<span data-ttu-id="ad409-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad409-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ad409-113">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="ad409-113">**Header:** None</span></span>  
<span data-ttu-id="ad409-114">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="ad409-114">**Library:** None</span></span>  
<span data-ttu-id="ad409-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ad409-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ad409-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad409-116">See also</span></span>

- [<span data-ttu-id="ad409-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ad409-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="ad409-118">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad409-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
