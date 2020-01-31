---
title: 'ICorDebugVariableSymbol:: SetValue yöntemi'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: fe6b63e4c0706dd69478753b3512f606e73bee7c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790849"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="16229-102">ICorDebugVariableSymbol:: SetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="16229-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="16229-103">Bir bayt dizisinin değerini bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="16229-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16229-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16229-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="16229-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16229-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="16229-106">'ndaki Değişkenin değeri ayarlanacak başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="16229-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="16229-107">Bu parametre, bir nesnedeki üye alanlarına yazılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16229-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="16229-108">'ndaki Bağlamını yeni değeri yansıtacak şekilde güncellenmesi gereken iş parçacığının iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="16229-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="16229-109">'ndaki İş parçacığı bağlamının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="16229-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="16229-110">'ndaki Değeri yazmak için kullanılan iş parçacığı bağlamı.</span><span class="sxs-lookup"><span data-stu-id="16229-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="16229-111">'ndaki `pValue` arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="16229-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="16229-112">'ndaki Ayarlanacak değeri içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="16229-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16229-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16229-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16229-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16229-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16229-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16229-115">Requirements</span></span>  
 <span data-ttu-id="16229-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16229-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16229-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16229-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16229-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="16229-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16229-119">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16229-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16229-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16229-120">See also</span></span>

- [<span data-ttu-id="16229-121">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16229-121">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="16229-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="16229-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
