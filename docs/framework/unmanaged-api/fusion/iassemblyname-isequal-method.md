---
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
ms.openlocfilehash: 0fabf8159c2626d4e1716e3be60baaf1ec834032
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712995"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="e50e1-102">IAssemblyName::IsEqual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e50e1-102">IAssemblyName::IsEqual Method</span></span>

<span data-ttu-id="e50e1-103">Belirtilen bir [IAssemblyName](iassemblyname-interface.md) nesnesinin `IAssemblyName` , belirtilen karşılaştırma bayraklarını temel alarak bu değere eşit olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="e50e1-103">Determines whether a specified [IAssemblyName](iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e50e1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e50e1-104">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e50e1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e50e1-105">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="e50e1-106">'ndaki `IAssemblyName` Bu nesnenin karşılaştırılacağı nesne `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="e50e1-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="e50e1-107">'ndaki Karşılaştırmayı etkileyen [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="e50e1-107">[in] A bitwise combination of [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e50e1-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e50e1-108">Requirements</span></span>  

 <span data-ttu-id="e50e1-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e50e1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e50e1-110">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e50e1-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e50e1-111">**Net Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e50e1-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e50e1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e50e1-112">See also</span></span>

- [<span data-ttu-id="e50e1-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e50e1-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="e50e1-114">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="e50e1-114">Fusion Enumerations</span></span>](fusion-enumerations.md)
