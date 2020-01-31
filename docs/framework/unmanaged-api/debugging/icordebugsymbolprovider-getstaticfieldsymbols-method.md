---
title: 'ICorDebugSymbolProvider:: GetStaticFieldSymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: 02cc62a421058f83e28ce945ae9e76745f768988
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791562"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="226ed-102">ICorDebugSymbolProvider:: GetStaticFieldSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="226ed-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="226ed-103">TypeSpec imzasına karşılık gelen statik alan sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="226ed-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="226ed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="226ed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="226ed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="226ed-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="226ed-106">'ndaki `typeSig` dizisindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="226ed-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="226ed-107">'ndaki `typespec` imzasını içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="226ed-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="226ed-108">'ndaki İstenen simgelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="226ed-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="226ed-109">dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="226ed-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="226ed-110">dışı İstenen statik alan sembollerini içeren [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="226ed-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="226ed-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="226ed-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="226ed-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="226ed-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="226ed-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="226ed-113">Requirements</span></span>  
 <span data-ttu-id="226ed-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="226ed-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="226ed-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="226ed-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="226ed-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="226ed-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="226ed-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="226ed-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226ed-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="226ed-118">See also</span></span>

- [<span data-ttu-id="226ed-119">GetInstanceFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="226ed-119">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="226ed-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="226ed-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="226ed-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="226ed-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
