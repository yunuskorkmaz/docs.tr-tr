---
title: 'ICorDebugSymbolProvider:: GetMethodParameterSymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: 051002b547aaa9745ae4efb516211123089c3128
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379594"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="03475-102">ICorDebugSymbolProvider:: GetMethodParameterSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="03475-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="03475-103">Yöntemin parametre sembollerini, bu yöntemin göreli sanal adresi (RVA) verilen şekilde alır.</span><span class="sxs-lookup"><span data-stu-id="03475-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03475-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03475-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03475-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03475-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="03475-106">'ndaki Metodun yerel göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="03475-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="03475-107">'ndaki İstenen yerel semboller sayısı.</span><span class="sxs-lookup"><span data-stu-id="03475-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="03475-108">dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="03475-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="03475-109">dışı Metodun yerel sembollerini içeren [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="03475-109">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03475-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03475-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03475-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03475-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03475-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03475-112">Requirements</span></span>  
 <span data-ttu-id="03475-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03475-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03475-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="03475-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03475-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="03475-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03475-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03475-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03475-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03475-117">See also</span></span>

- [<span data-ttu-id="03475-118">GetMethodLocalSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03475-118">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="03475-119">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03475-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="03475-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="03475-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
