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
ms.openlocfilehash: e28fa73300e147ac07a2d325fbf517480bb73797
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394943"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="66c4b-102">IXCLRDataProcess:: Startenummethodınstancesbyaddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="66c4b-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="66c4b-103">Verilen bir adresten başlayarak Yöntem örneklerinin numaralandırılacağı bir tanıtıcı sağlar `AppDomain` .</span><span class="sxs-lookup"><span data-stu-id="66c4b-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="66c4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66c4b-104">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="66c4b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66c4b-105">Parameters</span></span>

`address`\
<span data-ttu-id="66c4b-106">'ndaki İlk yöntem örneğinin adresi.</span><span class="sxs-lookup"><span data-stu-id="66c4b-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="66c4b-107">'ndaki Yöntem örneklerinin AppDomain 'i.</span><span class="sxs-lookup"><span data-stu-id="66c4b-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="66c4b-108">dışı Metot örneklerini numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="66c4b-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="66c4b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66c4b-109">Remarks</span></span>

<span data-ttu-id="66c4b-110">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 28 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="66c4b-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="66c4b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66c4b-111">Requirements</span></span>

<span data-ttu-id="66c4b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66c4b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="66c4b-113">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="66c4b-113">**Header:** None</span></span>  
<span data-ttu-id="66c4b-114">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="66c4b-114">**Library:** None</span></span>  
<span data-ttu-id="66c4b-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="66c4b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="66c4b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66c4b-116">See also</span></span>

- [<span data-ttu-id="66c4b-117">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="66c4b-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="66c4b-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="66c4b-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="66c4b-119">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66c4b-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
