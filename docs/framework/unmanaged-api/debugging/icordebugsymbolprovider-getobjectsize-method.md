---
title: 'ICorDebugSymbolProvider:: GetObjectSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: a5c0fe6d73302abbfabe2272cc878d6fd8f5fdec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138813"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="9a8a0-102">ICorDebugSymbolProvider:: GetObjectSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a8a0-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="9a8a0-103">Nesnelerin TypeSpec imzasına göre nesne boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a8a0-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a8a0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a8a0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a8a0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a8a0-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="9a8a0-106">'ndaki TypeSpec imzasında bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="9a8a0-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="9a8a0-107">Tür Imza</span><span class="sxs-lookup"><span data-stu-id="9a8a0-107">typeSig</span></span>  
 <span data-ttu-id="9a8a0-108">'ndaki TypeSpec imzası.</span><span class="sxs-lookup"><span data-stu-id="9a8a0-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="9a8a0-109">dışı Nesnenin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9a8a0-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a8a0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a8a0-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a8a0-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a8a0-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a8a0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a8a0-112">Requirements</span></span>  
 <span data-ttu-id="9a8a0-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a8a0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a8a0-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9a8a0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a8a0-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9a8a0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a8a0-116">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a8a0-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a8a0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a8a0-117">See also</span></span>

- [<span data-ttu-id="9a8a0-118">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a8a0-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="9a8a0-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9a8a0-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
