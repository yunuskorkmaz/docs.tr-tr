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
ms.openlocfilehash: cd2a2821128ad9265e8a831f7b02792e6453b1ee
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213796"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="a3b9d-102">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3b9d-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="a3b9d-103">Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3b9d-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3b9d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a3b9d-104">Methods</span></span>  
  
|<span data-ttu-id="a3b9d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a3b9d-105">Method</span></span>|<span data-ttu-id="a3b9d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3b9d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3b9d-107">IsChild Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3b9d-107">IsChild Method</span></span>](icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="a3b9d-108">Geçerli çerçevenin bir alt çerçeve olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a3b9d-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="a3b9d-109">IsMatchingParentFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3b9d-109">IsMatchingParentFrame Method</span></span>](icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="a3b9d-110">Belirtilen çerçevenin geçerli çerçevenin üst öğesi olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a3b9d-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="a3b9d-111">GetStackParameterSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3b9d-111">GetStackParameterSize Method</span></span>](icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="a3b9d-112">X86 işletim sistemlerindeki yığındaki parametrelerin birikmiş boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3b9d-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3b9d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3b9d-113">Remarks</span></span>  
 <span data-ttu-id="a3b9d-114">Bu arabirim "ICorDebugNativeFrame" arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="a3b9d-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3b9d-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a3b9d-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3b9d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3b9d-116">Requirements</span></span>  
 <span data-ttu-id="a3b9d-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3b9d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3b9d-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a3b9d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3b9d-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a3b9d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3b9d-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3b9d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b9d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3b9d-121">See also</span></span>

- [<span data-ttu-id="a3b9d-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a3b9d-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a3b9d-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a3b9d-123">Debugging</span></span>](index.md)
