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
ms.openlocfilehash: d1673b6045a6344ee0eeadf4ec3003206f92cde4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415684"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="2e1b4-102">ICorDebugMetaDataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e1b4-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="2e1b4-103">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e1b4-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e1b4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2e1b4-104">Methods</span></span>  
  
|<span data-ttu-id="2e1b4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2e1b4-105">Method</span></span>|<span data-ttu-id="2e1b4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e1b4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e1b4-107">GetMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e1b4-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="2e1b4-108">Tam yolu, meta veri hata ayıklayıcı istenen işlemi tamamlamak için gereken bir birime geri dönmek için hata ayıklayıcı sorar.</span><span class="sxs-lookup"><span data-stu-id="2e1b4-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e1b4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e1b4-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e1b4-110">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2e1b4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e1b4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e1b4-111">Requirements</span></span>  
 <span data-ttu-id="2e1b4-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e1b4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e1b4-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e1b4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e1b4-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e1b4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e1b4-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e1b4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e1b4-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e1b4-116">See Also</span></span>  
 [<span data-ttu-id="2e1b4-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2e1b4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2e1b4-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2e1b4-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
