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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4f57f27ec92e7977b46ebfa5967b0590674d2a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113444"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="b74bd-102">ICorDebugILFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b74bd-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="b74bd-103">Icordebugılframe arabirimi öğesinin mantıksal uzantısı.</span><span class="sxs-lookup"><span data-stu-id="b74bd-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b74bd-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b74bd-104">Methods</span></span>  
  
|<span data-ttu-id="b74bd-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b74bd-105">Method</span></span>|<span data-ttu-id="b74bd-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b74bd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b74bd-107">EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b74bd-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="b74bd-108">Icordebugtypeenum nesneyi içeren alır <xref:System.Type> bu çerçeve parametreleri.</span><span class="sxs-lookup"><span data-stu-id="b74bd-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="b74bd-109">RemapFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b74bd-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="b74bd-110">Bir işlev düzenlendi, yeni MSIL uzaklık belirterek yeniden eşlemesi.</span><span class="sxs-lookup"><span data-stu-id="b74bd-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b74bd-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b74bd-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b74bd-112">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b74bd-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b74bd-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b74bd-113">Requirements</span></span>  
 <span data-ttu-id="b74bd-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b74bd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b74bd-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b74bd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b74bd-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b74bd-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b74bd-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b74bd-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b74bd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b74bd-118">See also</span></span>

- [<span data-ttu-id="b74bd-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b74bd-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
