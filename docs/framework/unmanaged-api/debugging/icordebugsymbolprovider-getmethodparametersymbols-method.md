---
description: ': ICorDebugSymbolProvider:: GetMethodParameterSymbols metodu hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: GetMethodParameterSymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: 6ca71c7427f89cf33c5710d26b56590dbea3d2e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659757"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="51d4a-103">ICorDebugSymbolProvider:: GetMethodParameterSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="51d4a-103">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>

<span data-ttu-id="51d4a-104">Yöntemin parametre sembollerini, bu yöntemin göreli sanal adresi (RVA) verilen şekilde alır.</span><span class="sxs-lookup"><span data-stu-id="51d4a-104">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51d4a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51d4a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51d4a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51d4a-106">Parameters</span></span>  

 `nativeRVA`  
 <span data-ttu-id="51d4a-107">'ndaki Metodun yerel göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="51d4a-107">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="51d4a-108">'ndaki İstenen yerel semboller sayısı.</span><span class="sxs-lookup"><span data-stu-id="51d4a-108">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="51d4a-109">dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="51d4a-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="51d4a-110">dışı Metodun yerel sembollerini içeren [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="51d4a-110">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51d4a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51d4a-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51d4a-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="51d4a-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51d4a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51d4a-113">Requirements</span></span>  

 <span data-ttu-id="51d4a-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51d4a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51d4a-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="51d4a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51d4a-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="51d4a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51d4a-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51d4a-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51d4a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51d4a-118">See also</span></span>

- [<span data-ttu-id="51d4a-119">GetMethodLocalSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51d4a-119">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="51d4a-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51d4a-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="51d4a-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="51d4a-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
