---
title: 'ICorDebugSymbolProvider:: GetObjectSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: 4937ff1be7736f98be9efb9b01bdb322bf33e037
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730814"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="940cc-102">ICorDebugSymbolProvider:: GetObjectSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="940cc-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>

<span data-ttu-id="940cc-103">Nesnelerin TypeSpec imzasına göre nesne boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="940cc-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="940cc-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="940cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="940cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="940cc-105">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="940cc-106">'ndaki TypeSpec imzasında bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="940cc-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="940cc-107">Tür Imza</span><span class="sxs-lookup"><span data-stu-id="940cc-107">typeSig</span></span>  
 <span data-ttu-id="940cc-108">'ndaki TypeSpec imzası.</span><span class="sxs-lookup"><span data-stu-id="940cc-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="940cc-109">dışı Nesnenin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="940cc-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="940cc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="940cc-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="940cc-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="940cc-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="940cc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="940cc-112">Requirements</span></span>  

 <span data-ttu-id="940cc-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="940cc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="940cc-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="940cc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="940cc-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="940cc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="940cc-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="940cc-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="940cc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="940cc-117">See also</span></span>

- [<span data-ttu-id="940cc-118">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="940cc-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="940cc-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="940cc-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
