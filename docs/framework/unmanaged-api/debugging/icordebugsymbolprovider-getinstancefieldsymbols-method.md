---
title: 'ICorDebugSymbolProvider:: Getınstancefieldsymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 9ecc61ed6cac73a519f33e00cbfbfecc20ac2ebe
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379639"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="73fe0-102">ICorDebugSymbolProvider:: Getınstancefieldsymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="73fe0-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="73fe0-103">TypeSpec imzasına karşılık gelen örnek alanı sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="73fe0-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73fe0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73fe0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73fe0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73fe0-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="73fe0-106">'ndaki Dizideki bayt sayısı `typeSig` .</span><span class="sxs-lookup"><span data-stu-id="73fe0-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="73fe0-107">'ndaki İmzayı içeren bir bayt dizisi `typespec` .</span><span class="sxs-lookup"><span data-stu-id="73fe0-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="73fe0-108">'ndaki İstenen simgelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="73fe0-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="73fe0-109">dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="73fe0-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="73fe0-110">dışı İstenen örnek alanı sembollerini içeren bir [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="73fe0-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73fe0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73fe0-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73fe0-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73fe0-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73fe0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73fe0-113">Requirements</span></span>  
 <span data-ttu-id="73fe0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73fe0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73fe0-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73fe0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73fe0-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="73fe0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73fe0-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73fe0-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73fe0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73fe0-118">See also</span></span>

- [<span data-ttu-id="73fe0-119">GetStaticFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73fe0-119">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="73fe0-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73fe0-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="73fe0-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="73fe0-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
