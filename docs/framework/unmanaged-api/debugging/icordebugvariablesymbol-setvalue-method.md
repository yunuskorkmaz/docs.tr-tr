---
description: ': ICorDebugVariableSymbol:: SetValue yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugVariableSymbol:: SetValue yöntemi'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: aa36712defcf44039f17fe846113c15814549e09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800857"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="dd5d6-103">ICorDebugVariableSymbol:: SetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd5d6-103">ICorDebugVariableSymbol::SetValue Method</span></span>

<span data-ttu-id="dd5d6-104">Bir bayt dizisinin değerini bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="dd5d6-104">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd5d6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd5d6-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd5d6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd5d6-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="dd5d6-107">'ndaki Değişkenin değeri ayarlanacak başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="dd5d6-107">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="dd5d6-108">Bu parametre, bir nesnedeki üye alanlarına yazılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd5d6-108">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="dd5d6-109">'ndaki Bağlamını yeni değeri yansıtacak şekilde güncellenmesi gereken iş parçacığının iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="dd5d6-109">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="dd5d6-110">'ndaki İş parçacığı bağlamının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="dd5d6-110">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="dd5d6-111">'ndaki Değeri yazmak için kullanılan iş parçacığı bağlamı.</span><span class="sxs-lookup"><span data-stu-id="dd5d6-111">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="dd5d6-112">'ndaki Arabelleğin bayt cinsinden boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="dd5d6-112">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="dd5d6-113">'ndaki Ayarlanacak değeri içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="dd5d6-113">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd5d6-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd5d6-114">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd5d6-115">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd5d6-115">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd5d6-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd5d6-116">Requirements</span></span>  

 <span data-ttu-id="dd5d6-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd5d6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd5d6-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dd5d6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd5d6-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dd5d6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd5d6-120">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd5d6-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5d6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd5d6-121">See also</span></span>

- [<span data-ttu-id="dd5d6-122">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd5d6-122">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="dd5d6-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dd5d6-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
