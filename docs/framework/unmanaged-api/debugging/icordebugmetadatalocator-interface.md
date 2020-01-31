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
ms.openlocfilehash: dd31bf458dde043a04e24251cedcac585fd385f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793036"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="ad19f-102">ICorDebugMetaDataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad19f-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="ad19f-103">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad19f-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad19f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ad19f-104">Methods</span></span>  
  
|<span data-ttu-id="ad19f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ad19f-105">Method</span></span>|<span data-ttu-id="ad19f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad19f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad19f-107">GetMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad19f-107">GetMetaData Method</span></span>](icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="ad19f-108">Hata ayıklayıcının istenen bir işlemi tamamlaması için gereken meta verileri bir modülün tam yolunu döndürmesini ister.</span><span class="sxs-lookup"><span data-stu-id="ad19f-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad19f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad19f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad19f-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ad19f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad19f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad19f-111">Requirements</span></span>  
 <span data-ttu-id="ad19f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad19f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad19f-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ad19f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad19f-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ad19f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad19f-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad19f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad19f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad19f-116">See also</span></span>

- [<span data-ttu-id="ad19f-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ad19f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ad19f-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ad19f-118">Debugging</span></span>](index.md)
