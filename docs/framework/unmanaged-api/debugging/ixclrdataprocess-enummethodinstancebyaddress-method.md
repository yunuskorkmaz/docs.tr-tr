---
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
ms.openlocfilehash: 142099ae5cf9637cc28e8c82aabcd831cc8f0f52
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420805"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="03ae0-102">IXCLRDataProcess:: Enummethodınstancebyaddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="03ae0-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="03ae0-103">Bir adres uzaklığında başlayarak bu işlemin Yöntem örneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="03ae0-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="03ae0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="03ae0-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="03ae0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03ae0-105">Parameters</span></span>

`handle`\
<span data-ttu-id="03ae0-106">'ndaki Metot örneklerini numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="03ae0-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="03ae0-107">dışı Numaralandırılmış Yöntem örneği.</span><span class="sxs-lookup"><span data-stu-id="03ae0-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="03ae0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03ae0-108">Remarks</span></span>

<span data-ttu-id="03ae0-109">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 29. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="03ae0-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="03ae0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03ae0-110">Requirements</span></span>

<span data-ttu-id="03ae0-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03ae0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="03ae0-112">**Üst bilgi:** Hiçbiri **Kitaplığı:** hiçbiri **.NET Framework sürümler:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="03ae0-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="03ae0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03ae0-113">See also</span></span>

- [<span data-ttu-id="03ae0-114">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="03ae0-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="03ae0-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="03ae0-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="03ae0-116">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03ae0-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
