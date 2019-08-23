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
ms.openlocfilehash: 64cf11ec294486fdc14d424e731eac8e4745d892
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939862"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="79711-102">ICorDebugMetaDataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79711-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="79711-103">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="79711-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79711-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="79711-104">Methods</span></span>  
  
|<span data-ttu-id="79711-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="79711-105">Method</span></span>|<span data-ttu-id="79711-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79711-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79711-107">GetMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79711-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="79711-108">Hata ayıklayıcının istenen bir işlemi tamamlaması için gereken meta verileri bir modülün tam yolunu döndürmesini ister.</span><span class="sxs-lookup"><span data-stu-id="79711-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79711-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79711-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79711-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="79711-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79711-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79711-111">Requirements</span></span>  
 <span data-ttu-id="79711-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79711-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79711-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="79711-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79711-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="79711-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79711-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79711-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79711-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79711-116">See also</span></span>

- [<span data-ttu-id="79711-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="79711-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="79711-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="79711-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
