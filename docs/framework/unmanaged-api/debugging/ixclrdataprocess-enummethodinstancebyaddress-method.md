---
title: IXCLRDataProcess::EnumMethodInstanceByAddress yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b42939e8e64e75337478ace67a9a91c6a03a94e3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416204"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="6007b-102">IXCLRDataProcess::EnumMethodInstanceByAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="6007b-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="6007b-103">Bu işlem bir adresi uzaklıkta başlayan yöntemi örneklerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="6007b-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6007b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6007b-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

### <a name="parameters"></a><span data-ttu-id="6007b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6007b-105">Parameters</span></span>

<span data-ttu-id="6007b-106">`handle` [in] Yöntem örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="6007b-106">`handle` [in] A handle for enumerating the method instances.</span></span>

<span data-ttu-id="6007b-107">`mod` [out] Numaralandırılmış yöntemi örneği.</span><span class="sxs-lookup"><span data-stu-id="6007b-107">`mod` [out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="6007b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6007b-108">Remarks</span></span>

<span data-ttu-id="6007b-109">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 28 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="6007b-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="6007b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6007b-110">Requirements</span></span>

<span data-ttu-id="6007b-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6007b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="6007b-112">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="6007b-112">**Header:** None</span></span>   
<span data-ttu-id="6007b-113">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="6007b-113">**Library:** None</span></span>   
<span data-ttu-id="6007b-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6007b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="6007b-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6007b-115">See Also</span></span>
- [<span data-ttu-id="6007b-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6007b-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="6007b-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6007b-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="6007b-118">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="6007b-118">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
