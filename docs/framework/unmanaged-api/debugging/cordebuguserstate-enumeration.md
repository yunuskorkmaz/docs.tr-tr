---
title: CorDebugUserState Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: c142b9656af2031b10de239645da76835c435655
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789234"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="b2177-102">CorDebugUserState Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b2177-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="b2177-103">Bir iş parçacığının kullanıcı durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2177-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2177-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2177-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a><span data-ttu-id="b2177-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b2177-105">Members</span></span>  
  
|<span data-ttu-id="b2177-106">Değer</span><span class="sxs-lookup"><span data-stu-id="b2177-106">Value</span></span>|<span data-ttu-id="b2177-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2177-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="b2177-108">İş parçacığının sonlandırılması istendi.</span><span class="sxs-lookup"><span data-stu-id="b2177-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="b2177-109">İş parçacığını askıya alma istendi.</span><span class="sxs-lookup"><span data-stu-id="b2177-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="b2177-110">İş parçacığı arka planda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="b2177-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="b2177-111">İş parçacığı yürütmeyi başlatmadı.</span><span class="sxs-lookup"><span data-stu-id="b2177-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="b2177-112">İş parçacığı sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="b2177-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="b2177-113">İş parçacığı başka bir iş parçacığının bir görevi tamamlamasını bekliyor.</span><span class="sxs-lookup"><span data-stu-id="b2177-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="b2177-114">İş parçacığı askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="b2177-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="b2177-115">İş parçacığı güvenli olmayan bir noktada.</span><span class="sxs-lookup"><span data-stu-id="b2177-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="b2177-116">Diğer bir deyişle, iş parçacığı, atık toplamayı engelleyebileceği bir yürütme noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="b2177-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="b2177-117">Hata ayıklama olayları güvenli olmayan noktalarından gönderilebilir, ancak bir iş parçacığının güvenli olmayan bir noktada askıya alınması, iş parçacığı sürdürülene kadar kilitlenmeye neden olur.</span><span class="sxs-lookup"><span data-stu-id="b2177-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="b2177-118">Güvenli ve güvenli olmayan noktaları, tam zamanında (JıT) ve çöp toplama uygulamasıyla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b2177-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="b2177-119">İş parçacığı iş parçacığı havuzundan yapılır.</span><span class="sxs-lookup"><span data-stu-id="b2177-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2177-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2177-120">Remarks</span></span>  
 <span data-ttu-id="b2177-121">Bir iş parçacığının kullanıcı durumu, iş parçacığının hata ayıklayıcı tarafından incelediği durumdur.</span><span class="sxs-lookup"><span data-stu-id="b2177-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="b2177-122">Bir iş parçacığında Kullanıcı durumlarının bir birleşimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2177-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="b2177-123">Bir iş parçacığının kullanıcı durumunu almak için [ICorDebugThread:: GetUserState](icordebugthread-getuserstate-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2177-123">Use the [ICorDebugThread::GetUserState](icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2177-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2177-124">Requirements</span></span>  
 <span data-ttu-id="b2177-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2177-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2177-126">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2177-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2177-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b2177-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2177-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2177-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2177-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2177-129">See also</span></span>

- [<span data-ttu-id="b2177-130">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b2177-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
