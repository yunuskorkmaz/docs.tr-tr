---
title: ICorDebugSymbolProvider::GetObjectSize yöntemi
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbcdb5541fdd49944f462321dc24131a32a42391
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953770"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="7816b-102">ICorDebugSymbolProvider::GetObjectSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="7816b-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="7816b-103">Kendi TypeSpec'te imzasına bağlı bir nesne için nesne boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7816b-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7816b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7816b-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7816b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7816b-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="7816b-106">[in] TypeSpec'te imza bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7816b-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="7816b-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="7816b-107">typeSig</span></span>  
 <span data-ttu-id="7816b-108">[in] TypeSpec'te imzası.</span><span class="sxs-lookup"><span data-stu-id="7816b-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="7816b-109">[out] Nesnenin boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7816b-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7816b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7816b-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7816b-111">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7816b-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7816b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7816b-112">Requirements</span></span>  
 <span data-ttu-id="7816b-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7816b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7816b-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7816b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7816b-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7816b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7816b-116">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7816b-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7816b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7816b-117">See also</span></span>

- [<span data-ttu-id="7816b-118">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7816b-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="7816b-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7816b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
