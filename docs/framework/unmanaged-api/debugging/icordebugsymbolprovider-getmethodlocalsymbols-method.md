---
title: ICorDebugSymbolProvider::GetMethodLocalSymbols yöntemi
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44771536ad7cb225c341505d4878d0cb4f2bdba5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568510"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="2ddae-102">ICorDebugSymbolProvider::GetMethodLocalSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ddae-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="2ddae-103">Bu yöntemin göreli sanal adres (RVA) verilen bir yöntemin yerel simgelerini alır.</span><span class="sxs-lookup"><span data-stu-id="2ddae-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ddae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ddae-104">Syntax</span></span>  
  
```  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ddae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ddae-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="2ddae-106">[in] Yerel göreli sanal adres yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2ddae-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="2ddae-107">[in] İstenen yerel semboller sayısı.</span><span class="sxs-lookup"><span data-stu-id="2ddae-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="2ddae-108">[out] Yöntemi tarafından alınan simgelerin sayısını bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2ddae-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="2ddae-109">[out] Bir işaretçi bir [Icordebugvariablesymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) yöntemin yerel semboller içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="2ddae-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ddae-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ddae-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ddae-111">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2ddae-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ddae-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ddae-112">Requirements</span></span>  
 <span data-ttu-id="2ddae-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ddae-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ddae-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ddae-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ddae-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ddae-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ddae-116">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ddae-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ddae-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ddae-117">See also</span></span>
- [<span data-ttu-id="2ddae-118">GetMethodParameterSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ddae-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="2ddae-119">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ddae-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="2ddae-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2ddae-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
