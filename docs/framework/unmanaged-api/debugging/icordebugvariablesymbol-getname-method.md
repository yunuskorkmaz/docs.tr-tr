---
title: ICorDebugVariableSymbol::GetName yöntemi
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d01f8c3956298daee9f11c912406079d98964225
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465304"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="38f0f-102">ICorDebugVariableSymbol::GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="38f0f-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="38f0f-103">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="38f0f-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38f0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38f0f-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38f0f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38f0f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="38f0f-106">[in] Karakter sayısı `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="38f0f-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="38f0f-107">[out] Gerçekte yazılan karakter sayısı için bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="38f0f-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="38f0f-108">Değişken adını içeren bir karakter dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="38f0f-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38f0f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38f0f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38f0f-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="38f0f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38f0f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38f0f-111">Requirements</span></span>  
 <span data-ttu-id="38f0f-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38f0f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38f0f-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38f0f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38f0f-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38f0f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38f0f-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38f0f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f0f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38f0f-116">See also</span></span>
- [<span data-ttu-id="38f0f-117">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38f0f-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="38f0f-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="38f0f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
