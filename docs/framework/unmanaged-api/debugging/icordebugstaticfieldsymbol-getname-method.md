---
title: ICorDebugStaticFieldSymbol::GetName yöntemi
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5f52999c3f680fbccefe4681f83d473cdb86306
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206492"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="473cd-102">ICorDebugStaticFieldSymbol::GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="473cd-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="473cd-103">Statik alan adını alır.</span><span class="sxs-lookup"><span data-stu-id="473cd-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="473cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="473cd-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="473cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="473cd-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="473cd-106">[in] Karakter sayısı `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="473cd-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="473cd-107">[out] Gerçekte yazılan karakter sayısı için bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="473cd-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="473cd-108">[out] Döndürülen adını depolar bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="473cd-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="473cd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="473cd-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="473cd-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="473cd-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="473cd-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="473cd-111">Requirements</span></span>  
 <span data-ttu-id="473cd-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="473cd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="473cd-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="473cd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="473cd-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="473cd-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="473cd-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="473cd-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="473cd-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="473cd-116">See also</span></span>

- [<span data-ttu-id="473cd-117">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="473cd-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="473cd-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="473cd-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
