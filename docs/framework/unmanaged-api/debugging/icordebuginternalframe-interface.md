---
title: ICorDebugInternalFrame Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a1af92cbce84b674058ab2c8af2e15b0070dcd8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974763"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="2fa11-102">ICorDebugInternalFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2fa11-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="2fa11-103">Bir çalışma zamanı iç yığın çerçevesinde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2fa11-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="2fa11-104">Icordebugframe arabirimi öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="2fa11-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2fa11-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2fa11-105">Methods</span></span>  
  
|<span data-ttu-id="2fa11-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2fa11-106">Method</span></span>|<span data-ttu-id="2fa11-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa11-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2fa11-108">GetFrameType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2fa11-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="2fa11-109">Bu iç çerçeve türünü alır.</span><span class="sxs-lookup"><span data-stu-id="2fa11-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fa11-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fa11-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fa11-111">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2fa11-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fa11-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2fa11-112">Requirements</span></span>  
 <span data-ttu-id="2fa11-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fa11-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fa11-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fa11-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fa11-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fa11-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fa11-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fa11-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa11-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fa11-117">See also</span></span>
- [<span data-ttu-id="2fa11-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2fa11-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
