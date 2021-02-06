---
description: ': ICorDebugSymbolProvider:: GetStaticFieldSymbols yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: GetStaticFieldSymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: e95f77be86ef88a73ca4c833b242617a0d405e21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659718"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="cdc92-103">ICorDebugSymbolProvider:: GetStaticFieldSymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdc92-103">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>

<span data-ttu-id="cdc92-104">TypeSpec imzasına karşılık gelen statik alan sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="cdc92-104">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdc92-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cdc92-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdc92-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cdc92-106">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="cdc92-107">'ndaki Dizideki bayt sayısı `typeSig` .</span><span class="sxs-lookup"><span data-stu-id="cdc92-107">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="cdc92-108">'ndaki İmzayı içeren bir bayt dizisi `typespec` .</span><span class="sxs-lookup"><span data-stu-id="cdc92-108">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="cdc92-109">'ndaki İstenen simgelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="cdc92-109">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="cdc92-110">dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cdc92-110">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="cdc92-111">dışı İstenen statik alan sembollerini içeren [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cdc92-111">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdc92-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cdc92-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdc92-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdc92-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdc92-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdc92-114">Requirements</span></span>  

 <span data-ttu-id="cdc92-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdc92-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdc92-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cdc92-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdc92-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cdc92-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdc92-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdc92-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc92-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdc92-119">See also</span></span>

- [<span data-ttu-id="cdc92-120">GetInstanceFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdc92-120">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="cdc92-121">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdc92-121">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="cdc92-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cdc92-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
