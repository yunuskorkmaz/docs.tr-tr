---
title: 'ICorDebugSymbolProvider:: GetMethodParameterSymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: a940077e50ff251111ca6eedaee49401775644d3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791591"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="47f77-102">ICorDebugSymbolProvider:: GetMethodParameterSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="47f77-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="47f77-103">Yöntemin parametre sembollerini, bu yöntemin göreli sanal adresi (RVA) verilen şekilde alır.</span><span class="sxs-lookup"><span data-stu-id="47f77-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47f77-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47f77-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47f77-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47f77-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="47f77-106">'ndaki Metodun yerel göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="47f77-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="47f77-107">'ndaki İstenen yerel semboller sayısı.</span><span class="sxs-lookup"><span data-stu-id="47f77-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="47f77-108">dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="47f77-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="47f77-109">dışı Metodun yerel sembollerini içeren [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="47f77-109">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47f77-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47f77-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47f77-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47f77-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47f77-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47f77-112">Requirements</span></span>  
 <span data-ttu-id="47f77-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47f77-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47f77-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="47f77-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47f77-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="47f77-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47f77-116">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47f77-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f77-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47f77-117">See also</span></span>

- [<span data-ttu-id="47f77-118">GetMethodLocalSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47f77-118">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="47f77-119">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47f77-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="47f77-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="47f77-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
