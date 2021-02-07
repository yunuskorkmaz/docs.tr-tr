---
description: ': ICorDebugUnmanagedCallback arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugUnmanagedCallback Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
ms.openlocfilehash: 6d8aa398ff7121e360c3da66671781cd169b6228
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690554"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="58758-103">ICorDebugUnmanagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58758-103">ICorDebugUnmanagedCallback Interface</span></span>

<span data-ttu-id="58758-104">Ortak dil çalışma zamanı (CLR) ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="58758-104">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58758-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="58758-105">Methods</span></span>  
  
|<span data-ttu-id="58758-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="58758-106">Method</span></span>|<span data-ttu-id="58758-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58758-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58758-108">DebugEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58758-108">DebugEvent Method</span></span>](icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="58758-109">Hata ayıklayıcıyı yerel bir olayın harekete geçirildiğinde bildirir.</span><span class="sxs-lookup"><span data-stu-id="58758-109">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58758-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58758-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58758-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="58758-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58758-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58758-112">Requirements</span></span>  

 <span data-ttu-id="58758-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58758-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58758-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="58758-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58758-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="58758-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58758-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58758-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58758-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58758-117">See also</span></span>

- [<span data-ttu-id="58758-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="58758-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
