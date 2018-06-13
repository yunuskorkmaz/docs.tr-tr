---
title: ICorDebugSymbolProvider::GetObjectSize yöntemi
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1da526ac133604fa43081f86988459c4238517c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421509"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="3bdb8-102">ICorDebugSymbolProvider::GetObjectSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="3bdb8-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="3bdb8-103">TypeSpec'te imzası dayalı bir nesne için nesne boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3bdb8-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bdb8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3bdb8-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3bdb8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3bdb8-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="3bdb8-106">[in] TypeSpec'te imza bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="3bdb8-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="3bdb8-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="3bdb8-107">typeSig</span></span>  
 <span data-ttu-id="3bdb8-108">[in] TypeSpec'te imzası.</span><span class="sxs-lookup"><span data-stu-id="3bdb8-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="3bdb8-109">[out] Nesnenin boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3bdb8-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bdb8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3bdb8-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bdb8-111">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3bdb8-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bdb8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3bdb8-112">Requirements</span></span>  
 <span data-ttu-id="3bdb8-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bdb8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bdb8-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bdb8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bdb8-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bdb8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bdb8-116">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bdb8-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bdb8-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3bdb8-117">See Also</span></span>  
 [<span data-ttu-id="3bdb8-118">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bdb8-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="3bdb8-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3bdb8-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
