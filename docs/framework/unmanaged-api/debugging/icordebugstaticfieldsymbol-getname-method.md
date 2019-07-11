---
title: ICorDebugStaticFieldSymbol::GetName yöntemi
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01281e09533ba7196d3fa3e57c463636cfb0dd77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760826"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="306bb-102">ICorDebugStaticFieldSymbol::GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="306bb-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="306bb-103">Statik alan adını alır.</span><span class="sxs-lookup"><span data-stu-id="306bb-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="306bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="306bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="306bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="306bb-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="306bb-106">[in] Karakter sayısı `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="306bb-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="306bb-107">[out] Gerçekte yazılan karakter sayısı için bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="306bb-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="306bb-108">[out] Döndürülen adını depolar bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="306bb-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="306bb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="306bb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="306bb-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="306bb-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="306bb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="306bb-111">Requirements</span></span>  
 <span data-ttu-id="306bb-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="306bb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="306bb-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="306bb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="306bb-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="306bb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="306bb-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="306bb-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="306bb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="306bb-116">See also</span></span>

- [<span data-ttu-id="306bb-117">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="306bb-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="306bb-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="306bb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
