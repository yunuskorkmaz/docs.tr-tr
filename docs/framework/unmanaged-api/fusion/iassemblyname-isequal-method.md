---
description: ': IAssemblyName:: IsEqual Yöntemi hakkında daha fazla bilgi'
title: IAssemblyName::IsEqual Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
ms.openlocfilehash: f1bb0e26a217354e904ff79b397771d727a7a661
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760699"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="d6bf9-103">IAssemblyName::IsEqual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6bf9-103">IAssemblyName::IsEqual Method</span></span>

<span data-ttu-id="d6bf9-104">Belirtilen bir [IAssemblyName](iassemblyname-interface.md) nesnesinin `IAssemblyName` , belirtilen karşılaştırma bayraklarını temel alarak bu değere eşit olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d6bf9-104">Determines whether a specified [IAssemblyName](iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6bf9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6bf9-105">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6bf9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6bf9-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="d6bf9-107">'ndaki `IAssemblyName` Bu nesnenin karşılaştırılacağı nesne `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="d6bf9-107">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="d6bf9-108">'ndaki Karşılaştırmayı etkileyen [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="d6bf9-108">[in] A bitwise combination of [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6bf9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6bf9-109">Requirements</span></span>  

 <span data-ttu-id="d6bf9-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6bf9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6bf9-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d6bf9-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d6bf9-112">**Net Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6bf9-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6bf9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6bf9-113">See also</span></span>

- [<span data-ttu-id="d6bf9-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6bf9-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="d6bf9-115">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="d6bf9-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
