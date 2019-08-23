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
ms.openlocfilehash: 9764cdcd07a09f5192a8f43b9baa5be40305c40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910164"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="ec4b8-102">ICorDebugInternalFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec4b8-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="ec4b8-103">Yığında bir çalışma zamanı iç çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ec4b8-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="ec4b8-104">Bu arabirim, ICorDebugFrame arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="ec4b8-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec4b8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ec4b8-105">Methods</span></span>  
  
|<span data-ttu-id="ec4b8-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ec4b8-106">Method</span></span>|<span data-ttu-id="ec4b8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec4b8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec4b8-108">GetFrameType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec4b8-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="ec4b8-109">Bu iç çerçevenin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="ec4b8-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec4b8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec4b8-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec4b8-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ec4b8-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec4b8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec4b8-112">Requirements</span></span>  
 <span data-ttu-id="ec4b8-113">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec4b8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec4b8-114">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ec4b8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec4b8-115">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ec4b8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec4b8-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec4b8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4b8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec4b8-117">See also</span></span>

- [<span data-ttu-id="ec4b8-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ec4b8-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
