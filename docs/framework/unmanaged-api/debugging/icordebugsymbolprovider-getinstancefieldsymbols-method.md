---
title: ICorDebugSymbolProvider::GetInstanceFieldSymbols yöntemi
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 908d53acb9130173327149db95d2d6ec9abc3ae7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540851"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="1d4fc-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d4fc-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="1d4fc-103">Örnek TypeSpec'te imza karşılık gelen alan simgelerini alır.</span><span class="sxs-lookup"><span data-stu-id="1d4fc-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d4fc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d4fc-104">Syntax</span></span>  
  
```  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d4fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d4fc-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="1d4fc-106">[in] Bayt sayısı `typeSig` dizisi.</span><span class="sxs-lookup"><span data-stu-id="1d4fc-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="1d4fc-107">[in] İçeren bir bayt dizisi `typespec` imzası.</span><span class="sxs-lookup"><span data-stu-id="1d4fc-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="1d4fc-108">[in] İstenen sembolleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="1d4fc-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="1d4fc-109">[out] Yöntemi tarafından alınan simgelerin sayısını bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1d4fc-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="1d4fc-110">[out] Bir işaretçi bir [Icordebugstaticfieldsymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) istenen örnek alan simgeleri içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="1d4fc-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d4fc-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d4fc-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d4fc-112">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1d4fc-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d4fc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d4fc-113">Requirements</span></span>  
 <span data-ttu-id="1d4fc-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d4fc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d4fc-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d4fc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d4fc-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d4fc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d4fc-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d4fc-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d4fc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d4fc-118">See also</span></span>
- [<span data-ttu-id="1d4fc-119">GetStaticFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d4fc-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="1d4fc-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d4fc-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="1d4fc-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1d4fc-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
