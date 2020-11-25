---
title: 'ICorDebugSymbolProvider:: GetStaticFieldSymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: 09e68c751da6500c5580f4945e8dd1c486a09217
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698669"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="19954-102">ICorDebugSymbolProvider:: GetStaticFieldSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="19954-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>

<span data-ttu-id="19954-103">TypeSpec imzasına karşılık gelen statik alan sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="19954-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19954-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="19954-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19954-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19954-105">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="19954-106">'ndaki Dizideki bayt sayısı `typeSig` .</span><span class="sxs-lookup"><span data-stu-id="19954-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="19954-107">'ndaki İmzayı içeren bir bayt dizisi `typespec` .</span><span class="sxs-lookup"><span data-stu-id="19954-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="19954-108">'ndaki İstenen simgelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="19954-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="19954-109">dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="19954-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="19954-110">dışı İstenen statik alan sembollerini içeren [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="19954-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19954-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19954-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19954-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19954-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19954-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19954-113">Requirements</span></span>  

 <span data-ttu-id="19954-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19954-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19954-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="19954-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19954-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="19954-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19954-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19954-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19954-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19954-118">See also</span></span>

- [<span data-ttu-id="19954-119">GetInstanceFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19954-119">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="19954-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19954-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="19954-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="19954-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
