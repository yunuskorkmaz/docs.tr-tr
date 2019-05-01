---
title: ICorDebugVariableSymbol::SetValue yöntemi
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bfbadc5553e86b2db10d66298c8d24d2a0f8bde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946178"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="e6928-102">ICorDebugVariableSymbol::SetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6928-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="e6928-103">Bir bayt dizisi değeri bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="e6928-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6928-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6928-104">Syntax</span></span>  
  
```  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6928-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6928-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="e6928-106">[in] Değişkenin değerini ayarlamak, başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="e6928-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="e6928-107">Bu parametre, bir nesne üyesi alanlara yazılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e6928-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="e6928-108">[in] İş parçacığı tanımlayıcısı, iş parçacığı bağlamı yeni değeri gösterecek şekilde güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6928-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="e6928-109">[in] İş parçacığı içeriğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e6928-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="e6928-110">[in] Değeri yazmak için kullanılan iş parçacığı bağlamı.</span><span class="sxs-lookup"><span data-stu-id="e6928-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="e6928-111">[in] Bayt cinsinden boyutu `pValue` arabellek.</span><span class="sxs-lookup"><span data-stu-id="e6928-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e6928-112">[in] Ayarlanacak değer içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="e6928-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6928-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6928-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6928-114">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6928-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6928-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6928-115">Requirements</span></span>  
 <span data-ttu-id="e6928-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6928-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6928-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6928-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6928-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6928-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6928-119">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6928-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6928-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6928-120">See also</span></span>

- [<span data-ttu-id="e6928-121">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6928-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="e6928-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e6928-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
