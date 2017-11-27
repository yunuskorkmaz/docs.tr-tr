---
title: "ICorDebugVariableSymbol::GetValue yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 789bca88ea2f2d87ebfc73275b4a7569fcbe8cc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="424f7-102">ICorDebugVariableSymbol::GetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="424f7-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="424f7-103">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="424f7-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="424f7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="424f7-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="424f7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="424f7-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="424f7-106">[in] Değeri okunacak değişkeninde başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="424f7-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="424f7-107">Bu parametre, bir nesne üyesi alanlarında okunurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="424f7-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="424f7-108">[in] Bayt cinsinden boyutu `context` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="424f7-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="424f7-109">[in] Değeri okumak için kullanılan iş parçacığı bağlamı.</span><span class="sxs-lookup"><span data-stu-id="424f7-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="424f7-110">[in] Bayt cinsinden boyutu `pValue` arabellek.</span><span class="sxs-lookup"><span data-stu-id="424f7-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="424f7-111">[out] Gerçekte yazılan bayt sayısı `pValue` arabellek.</span><span class="sxs-lookup"><span data-stu-id="424f7-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="424f7-112">[out] Değişkenin değerini içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="424f7-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="424f7-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="424f7-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="424f7-114">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="424f7-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="424f7-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="424f7-115">Requirements</span></span>  
 <span data-ttu-id="424f7-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="424f7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="424f7-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="424f7-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="424f7-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="424f7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="424f7-119">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="424f7-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="424f7-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="424f7-120">See Also</span></span>  
 [<span data-ttu-id="424f7-121">ICorDebugVariableSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="424f7-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="424f7-122">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="424f7-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
