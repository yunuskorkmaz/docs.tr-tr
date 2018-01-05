---
title: "ICorDebugInstanceFieldSymbol::GetName yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7071a640a5d3f379a03c45605cd6b3eb23c093ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="550b7-102">ICorDebugInstanceFieldSymbol::GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="550b7-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="550b7-103">Örnek alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="550b7-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="550b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="550b7-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="550b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="550b7-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="550b7-106">[in] Karakter sayısını `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="550b7-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="550b7-107">[out] Gerçekte yazılan karakter sayısını gösteren bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="550b7-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="550b7-108">[out] Döndürülen adını depolar bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="550b7-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="550b7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="550b7-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="550b7-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="550b7-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="550b7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="550b7-111">Requirements</span></span>  
 <span data-ttu-id="550b7-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="550b7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="550b7-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="550b7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="550b7-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="550b7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="550b7-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="550b7-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="550b7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="550b7-116">See Also</span></span>  
 [<span data-ttu-id="550b7-117">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="550b7-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="550b7-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="550b7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
