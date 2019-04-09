---
title: ICorDebugMetaDataLocator Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator
helpviewer_keywords:
- ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e9b9221aa2f5e048a94c225660ba2ac9214549c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108842"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="50e56-102">ICorDebugMetaDataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50e56-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="50e56-103">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="50e56-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50e56-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="50e56-104">Methods</span></span>  
  
|<span data-ttu-id="50e56-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="50e56-105">Method</span></span>|<span data-ttu-id="50e56-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50e56-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50e56-107">GetMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e56-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="50e56-108">Tam yolu, meta veri hata ayıklayıcı istenen bir işlemi tamamlamak için gereken bir birime geri dönmek için hata ayıklayıcı ister.</span><span class="sxs-lookup"><span data-stu-id="50e56-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50e56-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50e56-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50e56-110">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="50e56-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e56-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50e56-111">Requirements</span></span>  
 <span data-ttu-id="50e56-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50e56-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e56-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50e56-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50e56-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50e56-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="50e56-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="50e56-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="50e56-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50e56-116">See also</span></span>

- [<span data-ttu-id="50e56-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="50e56-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="50e56-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="50e56-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
