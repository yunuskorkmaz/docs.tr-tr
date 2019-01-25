---
title: ICorDebugInstanceFieldSymbol::GetName yöntemi
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64357f873c9f125712fce33a1d9995c79a8cc006
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533461"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="60019-102">ICorDebugInstanceFieldSymbol::GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="60019-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="60019-103">Örnek alanı adını alır.</span><span class="sxs-lookup"><span data-stu-id="60019-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60019-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60019-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60019-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60019-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="60019-106">[in] Karakter sayısı `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="60019-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="60019-107">[out] Gerçekte yazılan karakter sayısı için bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="60019-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="60019-108">[out] Döndürülen adını depolar bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="60019-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60019-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60019-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60019-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="60019-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60019-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60019-111">Requirements</span></span>  
 <span data-ttu-id="60019-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60019-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60019-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60019-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60019-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60019-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60019-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60019-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60019-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60019-116">See also</span></span>
- [<span data-ttu-id="60019-117">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60019-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="60019-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="60019-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
