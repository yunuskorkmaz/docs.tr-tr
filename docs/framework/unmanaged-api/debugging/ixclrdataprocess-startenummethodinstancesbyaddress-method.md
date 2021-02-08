---
description: 'Şu konuda daha fazla bilgi edinin: IXCLRDataProcess:: Startenummethodınstancesbyaddress yöntemi'
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
ms.openlocfilehash: 155d09192b60b8671435abb439f07dfbb290bc87
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800597"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="5881b-103">IXCLRDataProcess:: Startenummethodınstancesbyaddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="5881b-103">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="5881b-104">Verilen bir adresten başlayarak Yöntem örneklerinin numaralandırılacağı bir tanıtıcı sağlar `AppDomain` .</span><span class="sxs-lookup"><span data-stu-id="5881b-104">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5881b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5881b-105">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="5881b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5881b-106">Parameters</span></span>

`address`\
<span data-ttu-id="5881b-107">'ndaki İlk yöntem örneğinin adresi.</span><span class="sxs-lookup"><span data-stu-id="5881b-107">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="5881b-108">'ndaki Yöntem örneklerinin AppDomain 'i.</span><span class="sxs-lookup"><span data-stu-id="5881b-108">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="5881b-109">dışı Metot örneklerini numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="5881b-109">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="5881b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5881b-110">Remarks</span></span>

<span data-ttu-id="5881b-111">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 28 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="5881b-111">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="5881b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5881b-112">Requirements</span></span>

<span data-ttu-id="5881b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5881b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5881b-114">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="5881b-114">**Header:** None</span></span>  
<span data-ttu-id="5881b-115">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="5881b-115">**Library:** None</span></span>  
<span data-ttu-id="5881b-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5881b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5881b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5881b-117">See also</span></span>

- [<span data-ttu-id="5881b-118">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5881b-118">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="5881b-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5881b-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="5881b-120">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5881b-120">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
