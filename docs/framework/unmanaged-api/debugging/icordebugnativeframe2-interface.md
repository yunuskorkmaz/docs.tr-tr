---
title: ICorDebugNativeFrame2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 638ce7933ededf2ff7b03b1c5aed7f6bdbfebc6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912789"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="5e360-102">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e360-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="5e360-103">Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e360-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e360-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5e360-104">Methods</span></span>  
  
|<span data-ttu-id="5e360-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5e360-105">Method</span></span>|<span data-ttu-id="5e360-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e360-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e360-107">IsChild Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e360-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="5e360-108">Geçerli çerçevenin bir alt çerçeve olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="5e360-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="5e360-109">IsMatchingParentFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e360-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="5e360-110">Belirtilen çerçevenin geçerli çerçevenin üst öğesi olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="5e360-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="5e360-111">GetStackParameterSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e360-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="5e360-112">X86 işletim sistemlerindeki yığındaki parametrelerin birikmiş boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e360-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e360-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e360-113">Remarks</span></span>  
 <span data-ttu-id="5e360-114">Bu arabirim "ICorDebugNativeFrame" arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="5e360-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e360-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="5e360-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e360-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e360-116">Requirements</span></span>  
 <span data-ttu-id="5e360-117">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e360-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e360-118">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5e360-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e360-119">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5e360-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e360-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e360-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e360-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e360-121">See also</span></span>

- [<span data-ttu-id="5e360-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5e360-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5e360-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5e360-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
