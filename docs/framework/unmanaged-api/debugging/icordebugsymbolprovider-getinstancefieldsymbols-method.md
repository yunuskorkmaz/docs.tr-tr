---
description: ': ICorDebugSymbolProvider:: Getınstancefieldsymbols yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: Getınstancefieldsymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 379d943743bb1fe21edbcca2265b4d8613d4f4b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659900"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="64196-103">ICorDebugSymbolProvider:: Getınstancefieldsymbols yöntemi</span><span class="sxs-lookup"><span data-stu-id="64196-103">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>

<span data-ttu-id="64196-104">TypeSpec imzasına karşılık gelen örnek alanı sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="64196-104">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64196-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64196-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64196-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64196-106">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="64196-107">'ndaki Dizideki bayt sayısı `typeSig` .</span><span class="sxs-lookup"><span data-stu-id="64196-107">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="64196-108">'ndaki İmzayı içeren bir bayt dizisi `typespec` .</span><span class="sxs-lookup"><span data-stu-id="64196-108">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="64196-109">'ndaki İstenen simgelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="64196-109">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="64196-110">dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64196-110">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="64196-111">dışı İstenen örnek alanı sembollerini içeren bir [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64196-111">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64196-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64196-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64196-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="64196-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64196-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64196-114">Requirements</span></span>  

 <span data-ttu-id="64196-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64196-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64196-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="64196-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64196-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="64196-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64196-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64196-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64196-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64196-119">See also</span></span>

- [<span data-ttu-id="64196-120">GetStaticFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64196-120">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="64196-121">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64196-121">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="64196-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="64196-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
