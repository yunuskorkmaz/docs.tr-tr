---
title: 'ICorDebugVariableSymbol:: GetValue yöntemi'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: 2dc074384d209d0740a1fb0a9a16d96ff355f02b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790880"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="5c680-102">ICorDebugVariableSymbol:: GetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c680-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="5c680-103">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="5c680-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c680-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c680-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5c680-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c680-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="5c680-106">'ndaki Değerin okunacağı değişkenin başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="5c680-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="5c680-107">Bu parametre, bir nesnedeki üye alanlarını okurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c680-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="5c680-108">'ndaki `context` bağımsız değişkeninin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5c680-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="5c680-109">'ndaki Değeri okumak için kullanılan iş parçacığı bağlamı.</span><span class="sxs-lookup"><span data-stu-id="5c680-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="5c680-110">'ndaki `pValue` arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5c680-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="5c680-111">dışı Gerçekten `pValue` arabelleğine yazılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="5c680-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="5c680-112">dışı Değişkenin değerini içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="5c680-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c680-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c680-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c680-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5c680-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c680-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c680-115">Requirements</span></span>  
 <span data-ttu-id="5c680-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c680-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c680-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5c680-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c680-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5c680-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c680-119">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c680-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c680-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c680-120">See also</span></span>

- [<span data-ttu-id="5c680-121">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c680-121">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="5c680-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5c680-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
