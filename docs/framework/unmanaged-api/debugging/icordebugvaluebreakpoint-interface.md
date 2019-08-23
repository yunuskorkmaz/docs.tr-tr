---
title: ICorDebugValueBreakpoint Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f77268e069d322d0f491f78b154cf63b691e3e38
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966824"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="1e8a3-102">ICorDebugValueBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e8a3-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="1e8a3-103">Belirli değerlere erişim sağlamak için ICorDebugBreakpoint arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="1e8a3-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e8a3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1e8a3-104">Methods</span></span>  
  
|<span data-ttu-id="1e8a3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1e8a3-105">Method</span></span>|<span data-ttu-id="1e8a3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e8a3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e8a3-107">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e8a3-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="1e8a3-108">Kesme noktasının ayarlandığı nesnenin değerini temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="1e8a3-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e8a3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e8a3-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e8a3-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="1e8a3-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e8a3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e8a3-111">Requirements</span></span>  
 <span data-ttu-id="1e8a3-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e8a3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e8a3-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1e8a3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e8a3-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1e8a3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e8a3-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e8a3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e8a3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e8a3-116">See also</span></span>

- [<span data-ttu-id="1e8a3-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1e8a3-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
