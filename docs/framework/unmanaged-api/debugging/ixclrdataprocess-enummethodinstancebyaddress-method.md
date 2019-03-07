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
ms.openlocfilehash: 23b567e4119578fba2f8cd4ba47f66dcf56a3878
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496852"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="2a202-102">IXCLRDataProcess::EnumMethodInstanceByAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a202-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="2a202-103">Bu işlem bir adresi uzaklıkta başlayan yöntemi örneklerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="2a202-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2a202-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a202-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="2a202-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a202-105">Parameters</span></span>

`handle`\
<span data-ttu-id="2a202-106">[in] Yöntem örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="2a202-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="2a202-107">[out] Numaralandırılmış yöntemi örneği.</span><span class="sxs-lookup"><span data-stu-id="2a202-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a202-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a202-108">Remarks</span></span>

<span data-ttu-id="2a202-109">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 28 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="2a202-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2a202-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a202-110">Requirements</span></span>

<span data-ttu-id="2a202-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a202-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="2a202-112">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="2a202-112">**Header:** None</span></span>   
<span data-ttu-id="2a202-113">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="2a202-113">**Library:** None</span></span>   
<span data-ttu-id="2a202-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2a202-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="2a202-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a202-115">See also</span></span>
- [<span data-ttu-id="2a202-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2a202-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="2a202-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2a202-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="2a202-118">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a202-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
