---
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
ms.openlocfilehash: ef8dbd5253c02355f85fba626fa7e68ed62df4bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686463"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="a51e7-102">ICorDebugProcess3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a51e7-102">ICorDebugProcess3 Interface</span></span>

<span data-ttu-id="a51e7-103">Özel hata ayıklayıcı bildirimlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="a51e7-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a51e7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a51e7-104">Methods</span></span>  
  
|<span data-ttu-id="a51e7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a51e7-105">Method</span></span>|<span data-ttu-id="a51e7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a51e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a51e7-107">SetEnableCustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a51e7-107">SetEnableCustomNotification Method</span></span>](icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="a51e7-108">Belirtilen türdeki özel hata ayıklayıcı bildirimlerini etkinleştir ve devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="a51e7-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a51e7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a51e7-109">Remarks</span></span>  

 <span data-ttu-id="a51e7-110">Bu arabirim, ICorDebugProcess ve ICorDebugProcess2 arabirimlerini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="a51e7-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a51e7-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a51e7-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a51e7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a51e7-112">Requirements</span></span>  

 <span data-ttu-id="a51e7-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a51e7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a51e7-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a51e7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a51e7-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a51e7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a51e7-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a51e7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a51e7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a51e7-117">See also</span></span>

- [<span data-ttu-id="a51e7-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a51e7-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a51e7-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a51e7-119">Debugging</span></span>](index.md)
