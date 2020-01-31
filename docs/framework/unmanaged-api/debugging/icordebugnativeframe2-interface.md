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
ms.openlocfilehash: 22a3f39bc1f9b4e6cad1db4fd0a6480b7c04e8fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792752"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="a564e-102">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a564e-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="a564e-103">Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a564e-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a564e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a564e-104">Methods</span></span>  
  
|<span data-ttu-id="a564e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a564e-105">Method</span></span>|<span data-ttu-id="a564e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a564e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a564e-107">IsChild Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a564e-107">IsChild Method</span></span>](icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="a564e-108">Geçerli çerçevenin bir alt çerçeve olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a564e-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="a564e-109">IsMatchingParentFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a564e-109">IsMatchingParentFrame Method</span></span>](icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="a564e-110">Belirtilen çerçevenin geçerli çerçevenin üst öğesi olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a564e-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="a564e-111">GetStackParameterSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a564e-111">GetStackParameterSize Method</span></span>](icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="a564e-112">X86 işletim sistemlerindeki yığındaki parametrelerin birikmiş boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a564e-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a564e-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a564e-113">Remarks</span></span>  
 <span data-ttu-id="a564e-114">Bu arabirim "ICorDebugNativeFrame" arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="a564e-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a564e-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a564e-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a564e-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a564e-116">Requirements</span></span>  
 <span data-ttu-id="a564e-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a564e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a564e-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a564e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a564e-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a564e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a564e-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a564e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a564e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a564e-121">See also</span></span>

- [<span data-ttu-id="a564e-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a564e-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a564e-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a564e-123">Debugging</span></span>](index.md)
