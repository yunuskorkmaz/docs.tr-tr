---
title: ICorDebugMetaDataLocator Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dead97961713f2d19147e242a6161aa9477905a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="cffcd-102">ICorDebugMetaDataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cffcd-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="cffcd-103">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="cffcd-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cffcd-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cffcd-104">Methods</span></span>  
  
|<span data-ttu-id="cffcd-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cffcd-105">Method</span></span>|<span data-ttu-id="cffcd-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cffcd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cffcd-107">GetMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cffcd-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="cffcd-108">Tam yolu, meta veri hata ayıklayıcı istenen işlemi tamamlamak için gereken bir birime geri dönmek için hata ayıklayıcı sorar.</span><span class="sxs-lookup"><span data-stu-id="cffcd-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cffcd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cffcd-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cffcd-110">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cffcd-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cffcd-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cffcd-111">Requirements</span></span>  
 <span data-ttu-id="cffcd-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cffcd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cffcd-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cffcd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cffcd-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cffcd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cffcd-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cffcd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cffcd-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cffcd-116">See Also</span></span>  
 [<span data-ttu-id="cffcd-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cffcd-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="cffcd-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cffcd-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
