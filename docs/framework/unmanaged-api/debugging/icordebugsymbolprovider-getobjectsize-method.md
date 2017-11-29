---
title: "ICorDebugSymbolProvider::GetObjectSize yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ea9e0fcae9f98869884ad887a6c24de342512b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="d5cfc-102">ICorDebugSymbolProvider::GetObjectSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5cfc-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="d5cfc-103">TypeSpec'te imzası dayalı bir nesne için nesne boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5cfc-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5cfc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5cfc-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5cfc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5cfc-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="d5cfc-106">[in] TypeSpec'te imza bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="d5cfc-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="d5cfc-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="d5cfc-107">typeSig</span></span>  
 <span data-ttu-id="d5cfc-108">[in] TypeSpec'te imzası.</span><span class="sxs-lookup"><span data-stu-id="d5cfc-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="d5cfc-109">[out] Nesnenin boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5cfc-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5cfc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5cfc-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5cfc-111">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5cfc-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5cfc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5cfc-112">Requirements</span></span>  
 <span data-ttu-id="d5cfc-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5cfc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5cfc-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5cfc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5cfc-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5cfc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5cfc-116">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5cfc-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5cfc-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5cfc-117">See Also</span></span>  
 [<span data-ttu-id="d5cfc-118">ICorDebugSymbolProvider arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5cfc-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="d5cfc-119">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d5cfc-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
