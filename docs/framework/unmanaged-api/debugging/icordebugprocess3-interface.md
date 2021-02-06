---
description: 'Daha fazla bilgi edinin: ICorDebugProcess3 Interface'
title: ICorDebugProcess3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3
helpviewer_keywords:
- ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type:
- apiref
ms.openlocfilehash: 28b588bb4718f841e78b89ce44821971800b1f6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649981"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="0fd9c-103">ICorDebugProcess3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0fd9c-103">ICorDebugProcess3 Interface</span></span>

<span data-ttu-id="0fd9c-104">Özel hata ayıklayıcı bildirimlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="0fd9c-104">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0fd9c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0fd9c-105">Methods</span></span>  
  
|<span data-ttu-id="0fd9c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0fd9c-106">Method</span></span>|<span data-ttu-id="0fd9c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fd9c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0fd9c-108">SetEnableCustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0fd9c-108">SetEnableCustomNotification Method</span></span>](icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="0fd9c-109">Belirtilen türdeki özel hata ayıklayıcı bildirimlerini etkinleştir ve devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="0fd9c-109">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fd9c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0fd9c-110">Remarks</span></span>  

 <span data-ttu-id="0fd9c-111">Bu arabirim, ICorDebugProcess ve ICorDebugProcess2 arabirimlerini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="0fd9c-111">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0fd9c-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="0fd9c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fd9c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0fd9c-113">Requirements</span></span>  

 <span data-ttu-id="0fd9c-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fd9c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fd9c-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0fd9c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fd9c-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0fd9c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fd9c-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fd9c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd9c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fd9c-118">See also</span></span>

- [<span data-ttu-id="0fd9c-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0fd9c-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0fd9c-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0fd9c-120">Debugging</span></span>](index.md)
