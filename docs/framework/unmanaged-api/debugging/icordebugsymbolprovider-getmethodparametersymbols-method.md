---
title: ICorDebugSymbolProvider::GetMethodParameterSymbols yöntemi
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98efd1446c88c3a6c004b5a3254c9db835a43804
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953380"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="ca537-102">ICorDebugSymbolProvider::GetMethodParameterSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca537-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="ca537-103">Bu yöntemin göreli sanal adres (RVA) verilen bir yöntemin parametre simgelerini alır.</span><span class="sxs-lookup"><span data-stu-id="ca537-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca537-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca537-104">Syntax</span></span>  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca537-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca537-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="ca537-106">[in] Yerel göreli sanal adres yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ca537-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="ca537-107">[in] İstenen yerel semboller sayısı.</span><span class="sxs-lookup"><span data-stu-id="ca537-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="ca537-108">[out] Yöntemi tarafından alınan simgelerin sayısını bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ca537-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="ca537-109">[out] Bir işaretçi bir [Icordebugvariablesymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) yöntemin yerel semboller içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="ca537-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca537-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca537-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca537-111">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ca537-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca537-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca537-112">Requirements</span></span>  
 <span data-ttu-id="ca537-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca537-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca537-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca537-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca537-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca537-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca537-116">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca537-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca537-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca537-117">See also</span></span>

- [<span data-ttu-id="ca537-118">GetMethodLocalSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca537-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="ca537-119">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca537-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ca537-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ca537-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
