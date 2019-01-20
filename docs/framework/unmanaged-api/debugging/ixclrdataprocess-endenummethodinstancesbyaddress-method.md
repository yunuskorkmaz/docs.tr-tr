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
ms.openlocfilehash: a48a7fc9a141354666c50b1f6da8f1aaa180ff6c
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416164"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="27330-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="27330-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="27330-103">Örnek numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="27330-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="27330-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27330-104">Syntax</span></span>

```
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

### <a name="parameters"></a><span data-ttu-id="27330-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27330-105">Parameters</span></span>

<span data-ttu-id="27330-106">`handle` [out] Yöntem örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="27330-106">`handle` [out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="27330-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27330-107">Remarks</span></span>

<span data-ttu-id="27330-108">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 29 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="27330-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="27330-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27330-109">Requirements</span></span>

<span data-ttu-id="27330-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27330-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="27330-111">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="27330-111">**Header:** None</span></span>  
<span data-ttu-id="27330-112">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="27330-112">**Library:** None</span></span>  
<span data-ttu-id="27330-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="27330-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="27330-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27330-114">See Also</span></span>

- [<span data-ttu-id="27330-115">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="27330-115">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="27330-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="27330-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="27330-117">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="27330-117">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
