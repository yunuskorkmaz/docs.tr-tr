---
description: 'Daha fazla bilgi edinin: ICorDebugThread4 Interface'
title: ICorDebugThread4 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: 4ad587cee81ce635df0a8917b7a6d68e60aaf0b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800922"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="490ca-103">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="490ca-103">ICorDebugThread4 Interface</span></span>

<span data-ttu-id="490ca-104">İş parçacığı engelleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="490ca-104">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="490ca-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="490ca-105">Methods</span></span>  
  
|<span data-ttu-id="490ca-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="490ca-106">Method</span></span>|<span data-ttu-id="490ca-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="490ca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="490ca-108">GetBlockingObjects Yöntemi</span><span class="sxs-lookup"><span data-stu-id="490ca-108">GetBlockingObjects Method</span></span>](icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="490ca-109">İş parçacığı engelleme bilgileri sağlayan [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="490ca-109">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="490ca-110">HadUnhandledException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="490ca-110">HadUnhandledException Method</span></span>](icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="490ca-111">İş parçacığının işlenmeyen bir özel duruma sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="490ca-111">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="490ca-112">GetCurrentCustomDebuggerNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="490ca-112">GetCurrentCustomDebuggerNotification Method</span></span>](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="490ca-113">Geçerli iş parçacığında geçerli [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="490ca-113">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="490ca-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="490ca-114">Remarks</span></span>  

 <span data-ttu-id="490ca-115">Bu arabirim, ICorDebugThread, ICorDebugThread2 ve [ICorDebugThread3](icordebugthread3-interface.md) arabirimlerinin mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="490ca-115">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="490ca-116">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="490ca-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="490ca-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="490ca-117">Requirements</span></span>  

 <span data-ttu-id="490ca-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="490ca-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="490ca-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="490ca-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="490ca-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="490ca-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="490ca-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="490ca-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="490ca-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="490ca-122">See also</span></span>

- [<span data-ttu-id="490ca-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="490ca-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="490ca-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="490ca-124">Debugging</span></span>](index.md)
