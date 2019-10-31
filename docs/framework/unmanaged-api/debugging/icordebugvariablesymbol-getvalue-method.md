---
title: 'ICorDebugVariableSymbol:: GetValue yöntemi'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: 5ef7e67efb2bafd9b9f52203246fd7d1590e6107
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120958"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="2596b-102">ICorDebugVariableSymbol:: GetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="2596b-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="2596b-103">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="2596b-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2596b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2596b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2596b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2596b-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="2596b-106">'ndaki Değerin okunacağı değişkenin başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="2596b-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="2596b-107">Bu parametre, bir nesnedeki üye alanlarını okurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2596b-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="2596b-108">'ndaki `context` bağımsız değişkeninin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="2596b-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="2596b-109">'ndaki Değeri okumak için kullanılan iş parçacığı bağlamı.</span><span class="sxs-lookup"><span data-stu-id="2596b-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="2596b-110">'ndaki `pValue` arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="2596b-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="2596b-111">dışı Gerçekten `pValue` arabelleğine yazılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="2596b-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="2596b-112">dışı Değişkenin değerini içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="2596b-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2596b-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2596b-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2596b-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2596b-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2596b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2596b-115">Requirements</span></span>  
 <span data-ttu-id="2596b-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2596b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2596b-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2596b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2596b-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2596b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2596b-119">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2596b-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2596b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2596b-120">See also</span></span>

- [<span data-ttu-id="2596b-121">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2596b-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="2596b-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2596b-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
