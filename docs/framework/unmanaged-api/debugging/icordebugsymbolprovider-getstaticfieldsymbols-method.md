---
title: "ICorDebugSymbolProvider::GetStaticFieldSymbols yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3871a74ee2844835c09a6e395fd63536c7442261
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="1ca3f-102">ICorDebugSymbolProvider::GetStaticFieldSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ca3f-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="1ca3f-103">TypeSpec'te imza karşılık gelen statik alan simgelerini alır.</span><span class="sxs-lookup"><span data-stu-id="1ca3f-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ca3f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ca3f-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ca3f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ca3f-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="1ca3f-106">[in] Bayt sayısı `typeSig` dizi.</span><span class="sxs-lookup"><span data-stu-id="1ca3f-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="1ca3f-107">[in] İçeren bir bayt dizisi `typespec` imza.</span><span class="sxs-lookup"><span data-stu-id="1ca3f-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="1ca3f-108">[in] İstenen simgeleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="1ca3f-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="1ca3f-109">[out] Sembol yöntemi tarafından alınan sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1ca3f-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="1ca3f-110">[out] Bir işaretçi bir [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) istenen statik alan simgeleri içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="1ca3f-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ca3f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ca3f-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ca3f-112">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1ca3f-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ca3f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ca3f-113">Requirements</span></span>  
 <span data-ttu-id="1ca3f-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ca3f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ca3f-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ca3f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ca3f-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ca3f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ca3f-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ca3f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca3f-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ca3f-118">See Also</span></span>  
 [<span data-ttu-id="1ca3f-119">GetInstanceFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ca3f-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)  
 [<span data-ttu-id="1ca3f-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ca3f-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="1ca3f-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1ca3f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
