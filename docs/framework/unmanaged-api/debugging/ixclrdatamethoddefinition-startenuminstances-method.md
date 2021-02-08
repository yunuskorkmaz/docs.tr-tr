---
description: 'Şu konuda daha fazla bilgi edinin: IXCLRDataMethodDefinition:: Startenumınstances yöntemi'
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
ms.openlocfilehash: 74de6360c90766cfec17e6b88a495fe2a70858b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800831"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="debf6-103">IXCLRDataMethodDefinition:: Startenumınstances yöntemi</span><span class="sxs-lookup"><span data-stu-id="debf6-103">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="debf6-104">Belirli bir için yöntem örneklerinin numaralandırması için bir tanıtıcı sağlar `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="debf6-104">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="debf6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="debf6-105">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="debf6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="debf6-106">Parameters</span></span>

`appDomain`\
<span data-ttu-id="debf6-107">'ndaki Sabit listesi için bir uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="debf6-107">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="debf6-108">dışı Örnekleri numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="debf6-108">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="debf6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="debf6-109">Remarks</span></span>

<span data-ttu-id="debf6-110">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataMethodDefinition` ve sanal yöntem tablosunun 5 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="debf6-110">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="debf6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="debf6-111">Requirements</span></span>

<span data-ttu-id="debf6-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="debf6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="debf6-113">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="debf6-113">**Header:** None</span></span>  
<span data-ttu-id="debf6-114">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="debf6-114">**Library:** None</span></span>  
<span data-ttu-id="debf6-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="debf6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="debf6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="debf6-116">See also</span></span>

- [<span data-ttu-id="debf6-117">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="debf6-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="debf6-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="debf6-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="debf6-119">IXCLRDataMethodDefinition Arabirimi</span><span class="sxs-lookup"><span data-stu-id="debf6-119">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
