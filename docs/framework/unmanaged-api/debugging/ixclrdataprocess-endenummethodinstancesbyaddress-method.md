---
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
ms.openlocfilehash: 5960d08ccfc09010a20d28a22c2e2f3f5b339c7d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420834"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="1c90c-102">IXCLRDataProcess:: Endenummethodınstancesbyaddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c90c-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="1c90c-103">Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="1c90c-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1c90c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1c90c-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="1c90c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c90c-105">Parameters</span></span>

`handle`\
<span data-ttu-id="1c90c-106">dışı Metot örneklerini numaralandırmak için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="1c90c-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c90c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c90c-107">Remarks</span></span>

<span data-ttu-id="1c90c-108">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 30. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1c90c-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c90c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c90c-109">Requirements</span></span>

<span data-ttu-id="1c90c-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c90c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1c90c-111">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1c90c-111">**Header:** None</span></span>  
<span data-ttu-id="1c90c-112">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1c90c-112">**Library:** None</span></span>  
<span data-ttu-id="1c90c-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1c90c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1c90c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c90c-114">See also</span></span>

- [<span data-ttu-id="1c90c-115">CLRDataSourceType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1c90c-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="1c90c-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1c90c-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="1c90c-117">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c90c-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
