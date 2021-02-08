---
description: ': ICorDebugInternalFrame arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7143f270b97e10fb9664aa7f7387749ddecbbcc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791146"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="eab7f-103">ICorDebugInternalFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eab7f-103">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="eab7f-104">Yığında bir çalışma zamanı iç çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eab7f-104">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="eab7f-105">Bu arabirim, ICorDebugFrame arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="eab7f-105">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eab7f-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eab7f-106">Methods</span></span>  
  
|<span data-ttu-id="eab7f-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="eab7f-107">Method</span></span>|<span data-ttu-id="eab7f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eab7f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eab7f-109">GetFrameType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eab7f-109">GetFrameType Method</span></span>](icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="eab7f-110">Bu iç çerçevenin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="eab7f-110">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eab7f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eab7f-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eab7f-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="eab7f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab7f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eab7f-113">Requirements</span></span>  

 <span data-ttu-id="eab7f-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eab7f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eab7f-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eab7f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eab7f-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eab7f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eab7f-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eab7f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab7f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eab7f-118">See also</span></span>

- [<span data-ttu-id="eab7f-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eab7f-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
