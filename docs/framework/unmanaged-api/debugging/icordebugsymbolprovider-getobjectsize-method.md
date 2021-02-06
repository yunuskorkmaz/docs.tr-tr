---
description: ': ICorDebugSymbolProvider:: GetObjectSize yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: GetObjectSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: 72720a1af9958fd0ab91276b3967733cec77fee7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659717"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="ae9e4-103">ICorDebugSymbolProvider:: GetObjectSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae9e4-103">ICorDebugSymbolProvider::GetObjectSize Method</span></span>

<span data-ttu-id="ae9e4-104">Nesnelerin TypeSpec imzasına göre nesne boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ae9e4-104">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae9e4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae9e4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae9e4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae9e4-106">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="ae9e4-107">'ndaki TypeSpec imzasında bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ae9e4-107">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="ae9e4-108">Tür Imza</span><span class="sxs-lookup"><span data-stu-id="ae9e4-108">typeSig</span></span>  
 <span data-ttu-id="ae9e4-109">'ndaki TypeSpec imzası.</span><span class="sxs-lookup"><span data-stu-id="ae9e4-109">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="ae9e4-110">dışı Nesnenin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ae9e4-110">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae9e4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae9e4-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae9e4-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae9e4-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae9e4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae9e4-113">Requirements</span></span>  

 <span data-ttu-id="ae9e4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae9e4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae9e4-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ae9e4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae9e4-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ae9e4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae9e4-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae9e4-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae9e4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae9e4-118">See also</span></span>

- [<span data-ttu-id="ae9e4-119">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae9e4-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ae9e4-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ae9e4-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
