---
title: 'IXCLRDataMethodDefinition:: Startenumınstances yöntemi'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 84e0ad392c5fee8377115427482d80543454fff3
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397201"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="5ed6e-102">IXCLRDataMethodDefinition:: Startenumınstances yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ed6e-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="5ed6e-103">Belirli bir için yöntem örneklerinin numaralandırması için bir tanıtıcı sağlar `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="5ed6e-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5ed6e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ed6e-104">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="5ed6e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ed6e-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="5ed6e-106">'ndaki Sabit listesi için bir uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="5ed6e-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="5ed6e-107">dışı Örnekleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="5ed6e-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ed6e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ed6e-108">Remarks</span></span>

<span data-ttu-id="5ed6e-109">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataMethodDefinition` ve sanal yöntem tablosunun 5 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="5ed6e-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ed6e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ed6e-110">Requirements</span></span>

<span data-ttu-id="5ed6e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ed6e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5ed6e-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="5ed6e-112">**Header:** None</span></span>  
<span data-ttu-id="5ed6e-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="5ed6e-113">**Library:** None</span></span>  
<span data-ttu-id="5ed6e-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed6e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5ed6e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ed6e-115">See also</span></span>

- [<span data-ttu-id="5ed6e-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5ed6e-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="5ed6e-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5ed6e-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="5ed6e-118">IXCLRDataMethodDefinition Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ed6e-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
