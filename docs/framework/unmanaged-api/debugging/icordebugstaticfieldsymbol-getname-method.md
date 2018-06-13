---
title: ICorDebugStaticFieldSymbol::GetName yöntemi
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 095c84a5cb448803bbfa45e0fad8a494343ca7f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422324"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="2aba0-102">ICorDebugStaticFieldSymbol::GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="2aba0-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="2aba0-103">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="2aba0-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aba0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2aba0-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2aba0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2aba0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2aba0-106">[in] Karakter sayısını `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="2aba0-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2aba0-107">[out] Gerçekte yazılan karakter sayısını gösteren bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="2aba0-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="2aba0-108">[out] Döndürülen adını depolar bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="2aba0-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2aba0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2aba0-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2aba0-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2aba0-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aba0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2aba0-111">Requirements</span></span>  
 <span data-ttu-id="2aba0-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2aba0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aba0-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2aba0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2aba0-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2aba0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2aba0-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aba0-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aba0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2aba0-116">See Also</span></span>  
 [<span data-ttu-id="2aba0-117">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2aba0-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="2aba0-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2aba0-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
