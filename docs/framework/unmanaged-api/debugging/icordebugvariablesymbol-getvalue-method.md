---
title: ICorDebugVariableSymbol::GetValue yöntemi
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 186d9eec0aa6ad9e327b1dd4d0f19e251c79ecf9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946191"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="a392b-102">ICorDebugVariableSymbol::GetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="a392b-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="a392b-103">Bir bayt dizisi olarak bir değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="a392b-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a392b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a392b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a392b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a392b-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="a392b-106">[in] Değer okunacağı değişkeninde başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="a392b-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="a392b-107">Bu parametre, bir nesne üyesi alanlarına okuma sırasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a392b-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="a392b-108">[in] Bayt cinsinden boyutu `context` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="a392b-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="a392b-109">[in] Değeri okumak için kullanılan iş parçacığı bağlamı.</span><span class="sxs-lookup"><span data-stu-id="a392b-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="a392b-110">[in] Bayt cinsinden boyutu `pValue` arabellek.</span><span class="sxs-lookup"><span data-stu-id="a392b-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="a392b-111">[out] Gerçekte yazılan bayt sayısı `pValue` arabellek.</span><span class="sxs-lookup"><span data-stu-id="a392b-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="a392b-112">[out] Değişkenin değerini içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="a392b-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a392b-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a392b-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a392b-114">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a392b-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a392b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a392b-115">Requirements</span></span>  
 <span data-ttu-id="a392b-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a392b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a392b-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a392b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a392b-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a392b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a392b-119">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a392b-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a392b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a392b-120">See also</span></span>

- [<span data-ttu-id="a392b-121">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a392b-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="a392b-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a392b-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
