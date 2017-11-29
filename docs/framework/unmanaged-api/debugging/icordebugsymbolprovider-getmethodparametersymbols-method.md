---
title: "ICorDebugSymbolProvider::GetMethodParameterSymbols yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b0b55caec333bc1e69dae9eee59ba30b6671737
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="e26fe-102">ICorDebugSymbolProvider::GetMethodParameterSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="e26fe-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="e26fe-103">Bu yöntemin göreli sanal adres (RVA) verilen bir yöntemin parametre simgelerini alır.</span><span class="sxs-lookup"><span data-stu-id="e26fe-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e26fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e26fe-104">Syntax</span></span>  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e26fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e26fe-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="e26fe-106">[in] Yerel göreli sanal adresi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e26fe-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="e26fe-107">[in] İstenen yerel semboller sayısı.</span><span class="sxs-lookup"><span data-stu-id="e26fe-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="e26fe-108">[out] Sembol yöntemi tarafından alınan sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e26fe-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="e26fe-109">[out] Bir işaretçi bir [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) yöntemin yerel semboller içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="e26fe-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e26fe-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e26fe-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e26fe-111">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e26fe-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e26fe-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e26fe-112">Requirements</span></span>  
 <span data-ttu-id="e26fe-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e26fe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e26fe-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e26fe-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e26fe-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e26fe-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e26fe-116">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e26fe-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e26fe-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e26fe-117">See Also</span></span>  
 [<span data-ttu-id="e26fe-118">GetMethodLocalSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="e26fe-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)  
 [<span data-ttu-id="e26fe-119">ICorDebugSymbolProvider arabirimi</span><span class="sxs-lookup"><span data-stu-id="e26fe-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="e26fe-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e26fe-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
