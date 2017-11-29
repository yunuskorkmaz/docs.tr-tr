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
ms.openlocfilehash: c33eaa36313f0cf6aae904761fb40bb2dbf9d753
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="f4b25-102">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4b25-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="f4b25-103">Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4b25-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4b25-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f4b25-104">Methods</span></span>  
  
|<span data-ttu-id="f4b25-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f4b25-105">Method</span></span>|<span data-ttu-id="f4b25-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4b25-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4b25-107">Ischild yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4b25-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="f4b25-108">Geçerli çerçeve alt çerçeve olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f4b25-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="f4b25-109">Ismatchingparentframe yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4b25-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="f4b25-110">Belirtilen çerçeve geçerli çerçevenin üst olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f4b25-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="f4b25-111">GetStackParameterSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4b25-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="f4b25-112">İşletim sistemleri x86 yığında parametreleri toplam boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4b25-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4b25-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4b25-113">Remarks</span></span>  
 <span data-ttu-id="f4b25-114">Bu arabirim, mantıksal olarak "ICorDebugNativeFrame" arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="f4b25-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4b25-115">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f4b25-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4b25-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4b25-116">Requirements</span></span>  
 <span data-ttu-id="f4b25-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4b25-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4b25-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4b25-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4b25-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4b25-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4b25-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4b25-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b25-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4b25-121">See Also</span></span>  
    
 [<span data-ttu-id="f4b25-122">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f4b25-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f4b25-123">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f4b25-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
