---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugVariableSymbol:: GetValue yöntemi'
title: 'ICorDebugVariableSymbol:: GetValue yöntemi'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: ccd7eae5cc4740e83d0210a903ba0e7778aa8896
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790574"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="abcc3-103">ICorDebugVariableSymbol:: GetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="abcc3-103">ICorDebugVariableSymbol::GetValue Method</span></span>

<span data-ttu-id="abcc3-104">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="abcc3-104">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abcc3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abcc3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abcc3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="abcc3-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="abcc3-107">'ndaki Değerin okunacağı değişkenin başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="abcc3-107">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="abcc3-108">Bu parametre, bir nesnedeki üye alanlarını okurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="abcc3-108">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="abcc3-109">'ndaki Bağımsız değişkenin bayt cinsinden boyutu `context` .</span><span class="sxs-lookup"><span data-stu-id="abcc3-109">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="abcc3-110">'ndaki Değeri okumak için kullanılan iş parçacığı bağlamı.</span><span class="sxs-lookup"><span data-stu-id="abcc3-110">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="abcc3-111">'ndaki Arabelleğin bayt cinsinden boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="abcc3-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="abcc3-112">dışı Gerçekte arabelleğe yazılan bayt sayısı `pValue` .</span><span class="sxs-lookup"><span data-stu-id="abcc3-112">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="abcc3-113">dışı Değişkenin değerini içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="abcc3-113">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abcc3-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abcc3-114">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abcc3-115">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="abcc3-115">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abcc3-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abcc3-116">Requirements</span></span>  

 <span data-ttu-id="abcc3-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abcc3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abcc3-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="abcc3-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abcc3-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="abcc3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abcc3-120">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abcc3-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abcc3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abcc3-121">See also</span></span>

- [<span data-ttu-id="abcc3-122">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abcc3-122">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="abcc3-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="abcc3-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
