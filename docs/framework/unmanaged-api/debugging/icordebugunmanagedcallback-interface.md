---
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
ms.openlocfilehash: dd5baa282d15d121b62b4dc4dd41bcf9ff393570
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395877"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="59381-102">ICorDebugUnmanagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59381-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="59381-103">Ortak dil çalışma zamanı (CLR) ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="59381-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59381-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="59381-104">Methods</span></span>  
  
|<span data-ttu-id="59381-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="59381-105">Method</span></span>|<span data-ttu-id="59381-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59381-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59381-107">DebugEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59381-107">DebugEvent Method</span></span>](icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="59381-108">Hata ayıklayıcıyı yerel bir olayın harekete geçirildiğinde bildirir.</span><span class="sxs-lookup"><span data-stu-id="59381-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59381-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59381-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59381-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="59381-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59381-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59381-111">Requirements</span></span>  
 <span data-ttu-id="59381-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59381-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59381-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="59381-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59381-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="59381-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59381-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59381-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59381-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59381-116">See also</span></span>

- [<span data-ttu-id="59381-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="59381-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
