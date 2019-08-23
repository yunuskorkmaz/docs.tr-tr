---
title: 'ICorDebugVariableSymbol:: GetName metodu'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23637055e493c008db36b23515001895450d6ab9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967898"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="ebc6e-102">ICorDebugVariableSymbol:: GetName metodu</span><span class="sxs-lookup"><span data-stu-id="ebc6e-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="ebc6e-103">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="ebc6e-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebc6e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebc6e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebc6e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ebc6e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ebc6e-106">'ndaki `szName` Arabellekteki karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="ebc6e-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ebc6e-107">dışı Gerçekte `szName` arabelleğe yazılan karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ebc6e-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ebc6e-108">Değişken adını içeren bir karakter dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ebc6e-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebc6e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebc6e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ebc6e-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ebc6e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebc6e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebc6e-111">Requirements</span></span>  
 <span data-ttu-id="ebc6e-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebc6e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebc6e-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ebc6e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebc6e-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ebc6e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebc6e-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebc6e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc6e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebc6e-116">See also</span></span>

- [<span data-ttu-id="ebc6e-117">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebc6e-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="ebc6e-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ebc6e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
