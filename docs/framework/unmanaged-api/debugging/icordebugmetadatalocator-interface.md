---
description: ': ICorDebugMetaDataLocator arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7b87527d4d0b98fc97631fb47184665daaf39edb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790834"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="a936c-103">ICorDebugMetaDataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a936c-103">ICorDebugMetaDataLocator Interface</span></span>

<span data-ttu-id="a936c-104">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a936c-104">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a936c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a936c-105">Methods</span></span>  
  
|<span data-ttu-id="a936c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a936c-106">Method</span></span>|<span data-ttu-id="a936c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a936c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a936c-108">GetMetaData Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a936c-108">GetMetaData Method</span></span>](icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="a936c-109">Hata ayıklayıcının istenen bir işlemi tamamlaması için gereken meta verileri bir modülün tam yolunu döndürmesini ister.</span><span class="sxs-lookup"><span data-stu-id="a936c-109">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a936c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a936c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a936c-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a936c-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a936c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a936c-112">Requirements</span></span>  

 <span data-ttu-id="a936c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a936c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a936c-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a936c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a936c-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a936c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a936c-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a936c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a936c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a936c-117">See also</span></span>

- [<span data-ttu-id="a936c-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a936c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a936c-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a936c-119">Debugging</span></span>](index.md)
