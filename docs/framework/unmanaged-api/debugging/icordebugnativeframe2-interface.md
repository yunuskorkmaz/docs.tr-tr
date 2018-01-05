---
title: ICorDebugNativeFrame2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2
helpviewer_keywords: ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f501d49f007e22c6f7db0e759ee19b40f87b4b33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="d4b22-102">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4b22-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="d4b22-103">Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4b22-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4b22-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d4b22-104">Methods</span></span>  
  
|<span data-ttu-id="d4b22-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d4b22-105">Method</span></span>|<span data-ttu-id="d4b22-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4b22-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4b22-107">IsChild Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4b22-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="d4b22-108">Geçerli çerçeve alt çerçeve olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d4b22-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="d4b22-109">IsMatchingParentFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4b22-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="d4b22-110">Belirtilen çerçeve geçerli çerçevenin üst olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d4b22-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="d4b22-111">GetStackParameterSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4b22-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="d4b22-112">İşletim sistemleri x86 yığında parametreleri toplam boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4b22-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4b22-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4b22-113">Remarks</span></span>  
 <span data-ttu-id="d4b22-114">Bu arabirim, mantıksal olarak "ICorDebugNativeFrame" arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="d4b22-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4b22-115">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d4b22-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4b22-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4b22-116">Requirements</span></span>  
 <span data-ttu-id="d4b22-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4b22-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4b22-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4b22-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4b22-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4b22-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4b22-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4b22-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b22-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4b22-121">See Also</span></span>  
    
 [<span data-ttu-id="d4b22-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d4b22-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d4b22-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d4b22-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
