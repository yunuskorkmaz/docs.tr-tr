---
title: IXCLRDataProcess::EndEnumMethodInstancesByAddress yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 67978e49a8c23c4b25234ecbb3639c696c7232f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655653"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="4ff1b-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ff1b-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="4ff1b-103">Örnek numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="4ff1b-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4ff1b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ff1b-104">Syntax</span></span>

```
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="4ff1b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ff1b-105">Parameters</span></span>

<span data-ttu-id="4ff1b-106">`handle` [out] Yöntem örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="4ff1b-106">`handle` [out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ff1b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ff1b-107">Remarks</span></span>

<span data-ttu-id="4ff1b-108">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 29 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="4ff1b-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4ff1b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ff1b-109">Requirements</span></span>

<span data-ttu-id="4ff1b-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ff1b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4ff1b-111">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="4ff1b-111">**Header:** None</span></span>  
<span data-ttu-id="4ff1b-112">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="4ff1b-112">**Library:** None</span></span>  
<span data-ttu-id="4ff1b-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4ff1b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4ff1b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ff1b-114">See also</span></span>

- [<span data-ttu-id="4ff1b-115">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4ff1b-115">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="4ff1b-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4ff1b-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="4ff1b-117">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ff1b-117">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
