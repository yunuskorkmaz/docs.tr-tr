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
ms.openlocfilehash: a51c709b0b331127b74d98c4dc42e2772fd7f2db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166445"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="966da-102">IXCLRDataProcess::EnumMethodInstanceByAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="966da-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="966da-103">Bu işlem bir adresi uzaklıkta başlayan yöntemi örneklerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="966da-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="966da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="966da-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="966da-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="966da-105">Parameters</span></span>

`handle`\
<span data-ttu-id="966da-106">[in] Yöntem örnekleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="966da-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="966da-107">[out] Numaralandırılmış yöntemi örneği.</span><span class="sxs-lookup"><span data-stu-id="966da-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="966da-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="966da-108">Remarks</span></span>

<span data-ttu-id="966da-109">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 28 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="966da-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="966da-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="966da-110">Requirements</span></span>

<span data-ttu-id="966da-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="966da-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="966da-112">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="966da-112">**Header:** None</span></span>   
<span data-ttu-id="966da-113">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="966da-113">**Library:** None</span></span>   
<span data-ttu-id="966da-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="966da-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="966da-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="966da-115">See also</span></span>

- [<span data-ttu-id="966da-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="966da-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="966da-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="966da-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="966da-118">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="966da-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
