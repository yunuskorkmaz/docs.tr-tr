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
ms.openlocfilehash: 1116945ae1a886f1b9491e0baf183e20c4fff177
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136625"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="8654c-102">ICorDebugMetaDataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8654c-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="8654c-103">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8654c-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8654c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8654c-104">Methods</span></span>  
  
|<span data-ttu-id="8654c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8654c-105">Method</span></span>|<span data-ttu-id="8654c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8654c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8654c-107">GetMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8654c-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="8654c-108">Hata ayıklayıcının istenen bir işlemi tamamlaması için gereken meta verileri bir modülün tam yolunu döndürmesini ister.</span><span class="sxs-lookup"><span data-stu-id="8654c-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8654c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8654c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8654c-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="8654c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8654c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8654c-111">Requirements</span></span>  
 <span data-ttu-id="8654c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8654c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8654c-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8654c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8654c-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8654c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8654c-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8654c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8654c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8654c-116">See also</span></span>

- [<span data-ttu-id="8654c-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8654c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8654c-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8654c-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
