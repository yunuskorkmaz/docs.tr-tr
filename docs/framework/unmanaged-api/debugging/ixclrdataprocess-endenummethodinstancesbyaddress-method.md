---
description: ': IXCLRDataProcess:: Endenummethodınstancesbyaddress yöntemi hakkında daha fazla bilgi edinin'
title: 'IXCLRDataProcess:: Endenummethodınstancesbyaddress yöntemi'
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
ms.openlocfilehash: 2e01fe0737319a7b336d9f6992bf81b2c57f9e70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800727"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="0f353-103">IXCLRDataProcess:: Endenummethodınstancesbyaddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f353-103">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="0f353-104">Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="0f353-104">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0f353-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f353-105">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="0f353-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f353-106">Parameters</span></span>

`handle`\
<span data-ttu-id="0f353-107">dışı Metot örneklerini numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="0f353-107">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f353-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f353-108">Remarks</span></span>

<span data-ttu-id="0f353-109">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 30. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="0f353-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f353-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f353-110">Requirements</span></span>

<span data-ttu-id="0f353-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f353-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0f353-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="0f353-112">**Header:** None</span></span>  
<span data-ttu-id="0f353-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="0f353-113">**Library:** None</span></span>  
<span data-ttu-id="0f353-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0f353-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0f353-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f353-115">See also</span></span>

- [<span data-ttu-id="0f353-116">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0f353-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="0f353-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0f353-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="0f353-118">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f353-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
