---
title: ICorDebugVariableSymbol::GetName yöntemi
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73aa5a9ca6625ab58e451449fab4c98f8b83014e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422446"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="a1732-102">ICorDebugVariableSymbol::GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1732-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="a1732-103">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="a1732-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1732-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1732-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1732-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1732-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="a1732-106">[in] Karakter sayısını `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="a1732-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a1732-107">[out] Gerçekte yazılan karakter sayısını gösteren bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="a1732-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="a1732-108">Değişken adı içeren bir karakter dizisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a1732-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1732-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1732-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1732-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a1732-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1732-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1732-111">Requirements</span></span>  
 <span data-ttu-id="a1732-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1732-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1732-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1732-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1732-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1732-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1732-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1732-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1732-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1732-116">See Also</span></span>  
 [<span data-ttu-id="a1732-117">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1732-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="a1732-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a1732-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
