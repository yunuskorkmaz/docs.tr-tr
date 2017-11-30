---
title: "ICorDebugSymbolProvider::GetInstanceFieldSymbols yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2ddb0b9e10314d027d342b34542129fbcdfb075
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="9b12b-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b12b-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="9b12b-103">Örnek TypeSpec'te imza karşılık gelen alan simgelerini alır.</span><span class="sxs-lookup"><span data-stu-id="9b12b-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b12b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b12b-104">Syntax</span></span>  
  
```  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b12b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b12b-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="9b12b-106">[in] Bayt sayısı `typeSig` dizi.</span><span class="sxs-lookup"><span data-stu-id="9b12b-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="9b12b-107">[in] İçeren bir bayt dizisi `typespec` imza.</span><span class="sxs-lookup"><span data-stu-id="9b12b-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="9b12b-108">[in] İstenen simgeleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="9b12b-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="9b12b-109">[out] Sembol yöntemi tarafından alınan sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9b12b-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="9b12b-110">[out] Bir işaretçi bir [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) istenen örneği alan simgeleri içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="9b12b-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b12b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b12b-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b12b-112">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9b12b-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b12b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b12b-113">Requirements</span></span>  
 <span data-ttu-id="9b12b-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b12b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b12b-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b12b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b12b-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b12b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b12b-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b12b-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b12b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b12b-118">See Also</span></span>  
 [<span data-ttu-id="9b12b-119">GetStaticFieldSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b12b-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)  
 [<span data-ttu-id="9b12b-120">ICorDebugSymbolProvider arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b12b-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="9b12b-121">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9b12b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
