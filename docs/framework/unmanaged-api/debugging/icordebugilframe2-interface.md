---
title: ICorDebugILFrame2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
ms.openlocfilehash: 08c2946a9bd6251f377ea594c0c3ca5d1bd98c67
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095085"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="6721c-102">ICorDebugILFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6721c-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="6721c-103">ICorDebugILFrame arabiriminin mantıksal uzantısı.</span><span class="sxs-lookup"><span data-stu-id="6721c-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6721c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6721c-104">Methods</span></span>  
  
|<span data-ttu-id="6721c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6721c-105">Method</span></span>|<span data-ttu-id="6721c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6721c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6721c-107">EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6721c-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="6721c-108">Bu çerçevede <xref:System.Type> parametrelerini içeren bir ICorDebugTypeEnum nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="6721c-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="6721c-109">RemapFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6721c-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="6721c-110">Yeni MSIL sapmasını belirterek düzenlenmiş bir işlevi yeniden eşler.</span><span class="sxs-lookup"><span data-stu-id="6721c-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6721c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6721c-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6721c-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="6721c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6721c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6721c-113">Requirements</span></span>  
 <span data-ttu-id="6721c-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6721c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6721c-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6721c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6721c-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6721c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6721c-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6721c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6721c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6721c-118">See also</span></span>

- [<span data-ttu-id="6721c-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6721c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
