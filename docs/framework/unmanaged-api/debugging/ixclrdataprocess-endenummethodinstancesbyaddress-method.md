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
ms.openlocfilehash: 072e775d11d44dfbca27f1616889e388ae61d467
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775485"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="7454a-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="7454a-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="7454a-103">Örnek numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="7454a-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7454a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7454a-104">Syntax</span></span>

```
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="7454a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7454a-105">Parameters</span></span>

`handle`\
<span data-ttu-id="7454a-106">[out] Yöntem örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="7454a-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="7454a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7454a-107">Remarks</span></span>

<span data-ttu-id="7454a-108">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 29 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="7454a-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7454a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7454a-109">Requirements</span></span>

<span data-ttu-id="7454a-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7454a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7454a-111">**Üst bilgi:** None</span><span class="sxs-lookup"><span data-stu-id="7454a-111">**Header:** None</span></span>  
<span data-ttu-id="7454a-112">**Kitaplığı:** None</span><span class="sxs-lookup"><span data-stu-id="7454a-112">**Library:** None</span></span>  
<span data-ttu-id="7454a-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7454a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7454a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7454a-114">See also</span></span>

- [<span data-ttu-id="7454a-115">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7454a-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="7454a-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7454a-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="7454a-117">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="7454a-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
