---
description: 'Daha fazla bilgi edinin: ICorDebugNativeFrame2 Interface'
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
ms.openlocfilehash: 9ed0e20bb29bef3b210258956ebecb1ee7a96df8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722353"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="c3ad4-103">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3ad4-103">ICorDebugNativeFrame2 Interface</span></span>

<span data-ttu-id="c3ad4-104">Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3ad4-104">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3ad4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c3ad4-105">Methods</span></span>  
  
|<span data-ttu-id="c3ad4-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c3ad4-106">Method</span></span>|<span data-ttu-id="c3ad4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3ad4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c3ad4-108">IsChild Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3ad4-108">IsChild Method</span></span>](icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="c3ad4-109">Geçerli çerçevenin bir alt çerçeve olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c3ad4-109">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="c3ad4-110">IsMatchingParentFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3ad4-110">IsMatchingParentFrame Method</span></span>](icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="c3ad4-111">Belirtilen çerçevenin geçerli çerçevenin üst öğesi olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c3ad4-111">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="c3ad4-112">GetStackParameterSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3ad4-112">GetStackParameterSize Method</span></span>](icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="c3ad4-113">X86 işletim sistemlerindeki yığındaki parametrelerin birikmiş boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3ad4-113">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3ad4-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3ad4-114">Remarks</span></span>  

 <span data-ttu-id="c3ad4-115">Bu arabirim "ICorDebugNativeFrame" arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="c3ad4-115">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3ad4-116">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="c3ad4-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3ad4-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3ad4-117">Requirements</span></span>  

 <span data-ttu-id="c3ad4-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3ad4-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3ad4-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c3ad4-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3ad4-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c3ad4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3ad4-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3ad4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ad4-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3ad4-122">See also</span></span>

- [<span data-ttu-id="c3ad4-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c3ad4-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c3ad4-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c3ad4-124">Debugging</span></span>](index.md)
