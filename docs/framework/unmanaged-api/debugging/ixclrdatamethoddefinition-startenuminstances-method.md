---
title: IXCLRDataMethodDefinition::StartEnumInstances yöntemi
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
ms.openlocfilehash: e92eea9677731756bdbfcbdcfac1531861fb5dce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961272"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="e4c03-102">IXCLRDataMethodDefinition::StartEnumInstances yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4c03-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="e4c03-103">Numaralandırma yöntemi örnekleri için bir tanıtıcı sağlayan bir verilen `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="e4c03-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e4c03-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4c03-104">Syntax</span></span>

```
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="e4c03-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4c03-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="e4c03-106">[in] AppDomain için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e4c03-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="e4c03-107">[out] Örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="e4c03-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4c03-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4c03-108">Remarks</span></span>

<span data-ttu-id="e4c03-109">Sağlanan yöntem parçasıdır `IXCLRDataMethodDefinition` arabirim ve sanal yöntem tablosunu üçüncü yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e4c03-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the third slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e4c03-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4c03-110">Requirements</span></span>

<span data-ttu-id="e4c03-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4c03-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e4c03-112">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="e4c03-112">**Header:** None</span></span>  
<span data-ttu-id="e4c03-113">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="e4c03-113">**Library:** None</span></span>  
<span data-ttu-id="e4c03-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e4c03-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e4c03-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4c03-115">See also</span></span>

- [<span data-ttu-id="e4c03-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e4c03-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="e4c03-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e4c03-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="e4c03-118">IXCLRDataMethodDefinition arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4c03-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)