---
title: 'IXCLRDataProcess:: Startenummethodınstancesbyaddress yöntemi'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 52d533f1c86b34b7b9febade8590e7ab58d8221e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420741"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="62db7-102">IXCLRDataProcess:: Startenummethodınstancesbyaddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="62db7-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="62db7-103">Verilen bir adresten başlayarak Yöntem örneklerinin numaralandırılacağı bir tanıtıcı sağlar `AppDomain` .</span><span class="sxs-lookup"><span data-stu-id="62db7-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="62db7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="62db7-104">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="62db7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62db7-105">Parameters</span></span>

`address`\
<span data-ttu-id="62db7-106">'ndaki İlk yöntem örneğinin adresi.</span><span class="sxs-lookup"><span data-stu-id="62db7-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="62db7-107">'ndaki Yöntem örneklerinin AppDomain 'i.</span><span class="sxs-lookup"><span data-stu-id="62db7-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="62db7-108">dışı Metot örneklerini numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="62db7-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="62db7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62db7-109">Remarks</span></span>

<span data-ttu-id="62db7-110">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 28 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="62db7-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="62db7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62db7-111">Requirements</span></span>

<span data-ttu-id="62db7-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62db7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="62db7-113">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="62db7-113">**Header:** None</span></span>  
<span data-ttu-id="62db7-114">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="62db7-114">**Library:** None</span></span>  
<span data-ttu-id="62db7-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="62db7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="62db7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62db7-116">See also</span></span>

- [<span data-ttu-id="62db7-117">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="62db7-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="62db7-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="62db7-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="62db7-119">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62db7-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
