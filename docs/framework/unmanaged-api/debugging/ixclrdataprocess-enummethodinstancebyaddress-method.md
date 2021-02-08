---
description: ': IXCLRDataProcess:: Enummethodınstancebyaddress yöntemi hakkında daha fazla bilgi edinin'
title: 'IXCLRDataProcess:: Enummethodınstancebyaddress yöntemi'
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
ms.openlocfilehash: a0d59956288e39be188628d10c63a52d09d17638
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800701"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="bd835-103">IXCLRDataProcess:: Enummethodınstancebyaddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd835-103">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="bd835-104">Bir adres uzaklığında başlayarak bu işlemin Yöntem örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="bd835-104">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bd835-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd835-105">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="bd835-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd835-106">Parameters</span></span>

`handle`\
<span data-ttu-id="bd835-107">'ndaki Metot örneklerini numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="bd835-107">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="bd835-108">dışı Numaralandırılmış Yöntem örneği.</span><span class="sxs-lookup"><span data-stu-id="bd835-108">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd835-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd835-109">Remarks</span></span>

<span data-ttu-id="bd835-110">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 29. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="bd835-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd835-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd835-111">Requirements</span></span>

<span data-ttu-id="bd835-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd835-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="bd835-113">**Üst bilgi:** Hiçbiri **Kitaplığı:** hiçbiri **.NET Framework sürümler:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bd835-113">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bd835-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd835-114">See also</span></span>

- [<span data-ttu-id="bd835-115">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bd835-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="bd835-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bd835-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="bd835-117">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd835-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
