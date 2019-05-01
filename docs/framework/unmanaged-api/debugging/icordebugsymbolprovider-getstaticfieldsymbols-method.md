---
title: ICorDebugSymbolProvider::GetStaticFieldSymbols yöntemi
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18bfab7a666a4c715b2236f5101bcceacb5b2fed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953336"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="ea1c0-102">ICorDebugSymbolProvider::GetStaticFieldSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea1c0-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="ea1c0-103">TypeSpec'te imza karşılık gelen statik alan simgelerini alır.</span><span class="sxs-lookup"><span data-stu-id="ea1c0-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea1c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea1c0-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea1c0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea1c0-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="ea1c0-106">[in] Bayt sayısı `typeSig` dizisi.</span><span class="sxs-lookup"><span data-stu-id="ea1c0-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="ea1c0-107">[in] İçeren bir bayt dizisi `typespec` imzası.</span><span class="sxs-lookup"><span data-stu-id="ea1c0-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="ea1c0-108">[in] İstenen sembolleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="ea1c0-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="ea1c0-109">[out] Yöntemi tarafından alınan simgelerin sayısını bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ea1c0-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="ea1c0-110">[out] Bir işaretçi bir [Icordebugstaticfieldsymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) istenen statik alan simgeleri içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="ea1c0-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea1c0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea1c0-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea1c0-112">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ea1c0-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea1c0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea1c0-113">Requirements</span></span>  
 <span data-ttu-id="ea1c0-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea1c0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea1c0-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea1c0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea1c0-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea1c0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea1c0-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea1c0-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea1c0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea1c0-118">See also</span></span>

- [<span data-ttu-id="ea1c0-119">GetInstanceFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea1c0-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="ea1c0-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea1c0-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ea1c0-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ea1c0-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
