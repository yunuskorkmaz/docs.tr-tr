---
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
ms.openlocfilehash: a0d6f3e109f92ad44eeeb1b1dec05e53015992a6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378357"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="693c7-102">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="693c7-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="693c7-103">İş parçacığı engelleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="693c7-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="693c7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="693c7-104">Methods</span></span>  
  
|<span data-ttu-id="693c7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="693c7-105">Method</span></span>|<span data-ttu-id="693c7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="693c7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="693c7-107">GetBlockingObjects Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693c7-107">GetBlockingObjects Method</span></span>](icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="693c7-108">İş parçacığı engelleme bilgileri sağlayan [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="693c7-108">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="693c7-109">HadUnhandledException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693c7-109">HadUnhandledException Method</span></span>](icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="693c7-110">İş parçacığının işlenmeyen bir özel duruma sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="693c7-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="693c7-111">GetCurrentCustomDebuggerNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693c7-111">GetCurrentCustomDebuggerNotification Method</span></span>](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="693c7-112">Geçerli iş parçacığında geçerli [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="693c7-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="693c7-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="693c7-113">Remarks</span></span>  
 <span data-ttu-id="693c7-114">Bu arabirim, ICorDebugThread, ICorDebugThread2 ve [ICorDebugThread3](icordebugthread3-interface.md) arabirimlerinin mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="693c7-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="693c7-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="693c7-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="693c7-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="693c7-116">Requirements</span></span>  
 <span data-ttu-id="693c7-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="693c7-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="693c7-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="693c7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="693c7-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="693c7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="693c7-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="693c7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="693c7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="693c7-121">See also</span></span>

- [<span data-ttu-id="693c7-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="693c7-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="693c7-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="693c7-123">Debugging</span></span>](index.md)
