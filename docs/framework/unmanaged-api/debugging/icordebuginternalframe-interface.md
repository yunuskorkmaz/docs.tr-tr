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
ms.openlocfilehash: b1ee5a155afa4e33340108e7295adef2309986cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122704"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="2fb0b-102">ICorDebugInternalFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2fb0b-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="2fb0b-103">Yığında bir çalışma zamanı iç çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2fb0b-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="2fb0b-104">Bu arabirim, ICorDebugFrame arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="2fb0b-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2fb0b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2fb0b-105">Methods</span></span>  
  
|<span data-ttu-id="2fb0b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2fb0b-106">Method</span></span>|<span data-ttu-id="2fb0b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fb0b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2fb0b-108">GetFrameType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2fb0b-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="2fb0b-109">Bu iç çerçevenin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="2fb0b-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fb0b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fb0b-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fb0b-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="2fb0b-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fb0b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2fb0b-112">Requirements</span></span>  
 <span data-ttu-id="2fb0b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fb0b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fb0b-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2fb0b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fb0b-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2fb0b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fb0b-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fb0b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fb0b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fb0b-117">See also</span></span>

- [<span data-ttu-id="2fb0b-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2fb0b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
