---
title: 'ICorDebugSymbolProvider:: GetStaticFieldSymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bd3442adf58250a423438666ec1092bab61958b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955548"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="5891b-102">ICorDebugSymbolProvider:: GetStaticFieldSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="5891b-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="5891b-103">TypeSpec imzasına karşılık gelen statik alan sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="5891b-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5891b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5891b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5891b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5891b-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="5891b-106">'ndaki `typeSig` Dizideki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="5891b-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="5891b-107">'ndaki `typespec` İmzayı içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="5891b-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="5891b-108">'ndaki İstenen simgelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="5891b-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="5891b-109">dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5891b-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="5891b-110">dışı İstenen statik alan sembollerini içeren [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5891b-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5891b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5891b-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5891b-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5891b-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5891b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5891b-113">Requirements</span></span>  
 <span data-ttu-id="5891b-114">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5891b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5891b-115">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5891b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5891b-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5891b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5891b-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5891b-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5891b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5891b-118">See also</span></span>

- [<span data-ttu-id="5891b-119">GetInstanceFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5891b-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="5891b-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5891b-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="5891b-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5891b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
