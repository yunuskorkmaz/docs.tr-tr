---
title: IXCLRDataProcess::EnumMethodInstanceByAddress Yöntemi
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
ms.openlocfilehash: afc5fc377dd45d5e8d4d2d7b3385ca0524df69e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176662"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="0eb88-102">IXCLRDataProcess::EnumMethodInstanceByAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0eb88-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="0eb88-103">Bir adres mahsup adresinden başlayan bu işlemin yöntem örneklerini dizir.</span><span class="sxs-lookup"><span data-stu-id="0eb88-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0eb88-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0eb88-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="0eb88-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0eb88-105">Parameters</span></span>

`handle`\
<span data-ttu-id="0eb88-106">[içinde] Yöntem örneklerini sayısallandırmak için bir tutamaç.</span><span class="sxs-lookup"><span data-stu-id="0eb88-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="0eb88-107">[çıkış] Numaralandırılmış yöntem örneği.</span><span class="sxs-lookup"><span data-stu-id="0eb88-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="0eb88-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0eb88-108">Remarks</span></span>

<span data-ttu-id="0eb88-109">Sağlanan yöntem `IXCLRDataProcess` arabirimin bir parçasıdır ve sanal yöntem tablosunun 28 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="0eb88-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0eb88-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0eb88-110">Requirements</span></span>

<span data-ttu-id="0eb88-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0eb88-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="0eb88-112">**Üstbilgi:** Yok **Kitaplık:** Yok **.NET Framework Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0eb88-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0eb88-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0eb88-113">See also</span></span>

- [<span data-ttu-id="0eb88-114">CLRDataSourceType Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="0eb88-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="0eb88-115">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0eb88-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="0eb88-116">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0eb88-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
