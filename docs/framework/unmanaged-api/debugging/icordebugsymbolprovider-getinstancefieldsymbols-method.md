---
title: 'ICorDebugSymbolProvider:: Getınstancefieldsymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 9c55ce4d36681e173047cfb51515a74899c5a9fe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791628"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="54f15-102">ICorDebugSymbolProvider:: Getınstancefieldsymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="54f15-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="54f15-103">TypeSpec imzasına karşılık gelen örnek alanı sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="54f15-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54f15-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54f15-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54f15-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54f15-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="54f15-106">'ndaki `typeSig` dizisindeki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="54f15-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="54f15-107">'ndaki `typespec` imzasını içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="54f15-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="54f15-108">'ndaki İstenen simgelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="54f15-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="54f15-109">dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="54f15-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="54f15-110">dışı İstenen örnek alanı sembollerini içeren bir [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="54f15-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54f15-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54f15-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54f15-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="54f15-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54f15-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54f15-113">Requirements</span></span>  
 <span data-ttu-id="54f15-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54f15-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54f15-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="54f15-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54f15-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="54f15-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54f15-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54f15-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54f15-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54f15-118">See also</span></span>

- [<span data-ttu-id="54f15-119">GetStaticFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54f15-119">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="54f15-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54f15-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="54f15-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="54f15-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
