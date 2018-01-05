---
title: "ICorDebugStaticFieldSymbol::GetName yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa999cf86c808e0fca430d181c0d9a9ba83f4a82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="47abb-102">ICorDebugStaticFieldSymbol::GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="47abb-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="47abb-103">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="47abb-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47abb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47abb-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47abb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47abb-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="47abb-106">[in] Karakter sayısını `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="47abb-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="47abb-107">[out] Gerçekte yazılan karakter sayısını gösteren bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="47abb-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="47abb-108">[out] Döndürülen adını depolar bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="47abb-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47abb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47abb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47abb-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47abb-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47abb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47abb-111">Requirements</span></span>  
 <span data-ttu-id="47abb-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47abb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47abb-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47abb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47abb-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47abb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47abb-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47abb-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47abb-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47abb-116">See Also</span></span>  
 [<span data-ttu-id="47abb-117">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47abb-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="47abb-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="47abb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
