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
ms.openlocfilehash: b0c37c666f23f04239ed827246b87c43ee8d5ad9
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420935"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="14bd6-102">IXCLRDataMethodDefinition:: Startenumınstances yöntemi</span><span class="sxs-lookup"><span data-stu-id="14bd6-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="14bd6-103">Belirli bir için yöntem örneklerinin numaralandırması için bir tanıtıcı sağlar `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="14bd6-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="14bd6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="14bd6-104">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="14bd6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14bd6-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="14bd6-106">'ndaki Sabit listesi için bir uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="14bd6-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="14bd6-107">dışı Örnekleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="14bd6-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="14bd6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14bd6-108">Remarks</span></span>

<span data-ttu-id="14bd6-109">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataMethodDefinition` ve sanal yöntem tablosunun 5 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="14bd6-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="14bd6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14bd6-110">Requirements</span></span>

<span data-ttu-id="14bd6-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14bd6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="14bd6-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="14bd6-112">**Header:** None</span></span>  
<span data-ttu-id="14bd6-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="14bd6-113">**Library:** None</span></span>  
<span data-ttu-id="14bd6-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="14bd6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="14bd6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14bd6-115">See also</span></span>

- [<span data-ttu-id="14bd6-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="14bd6-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="14bd6-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="14bd6-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="14bd6-118">IXCLRDataMethodDefinition Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14bd6-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
