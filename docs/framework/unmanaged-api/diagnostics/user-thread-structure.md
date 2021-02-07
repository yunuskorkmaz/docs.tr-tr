---
description: 'Daha fazla bilgi edinin: USER_THREAD yapısı'
title: USER_THREAD Yapısı
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
ms.openlocfilehash: a4bd22073b7610307e67107781bdb68a15ef795f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761275"
---
# <a name="user_thread-structure"></a><span data-ttu-id="e6769-103">USER_THREAD Yapısı</span><span class="sxs-lookup"><span data-stu-id="e6769-103">USER_THREAD Structure</span></span>

<span data-ttu-id="e6769-104">Bir iş parçacığı hakkındaki hata ayıklayıcıyla ilgili bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6769-104">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="e6769-105">Daha fazla bilgi için bkz. [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e6769-105">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6769-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e6769-106">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="e6769-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e6769-107">Members</span></span>  
  
|<span data-ttu-id="e6769-108">Üye</span><span class="sxs-lookup"><span data-stu-id="e6769-108">Member</span></span>|<span data-ttu-id="e6769-109">Description</span><span class="sxs-lookup"><span data-stu-id="e6769-109">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="e6769-110">İş parçacığı arabelleğinin adresi.</span><span class="sxs-lookup"><span data-stu-id="e6769-110">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="e6769-111">İş parçacığı arabelleğinin bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="e6769-111">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="e6769-112">İş parçacığı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e6769-112">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6769-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6769-113">Requirements</span></span>  

 <span data-ttu-id="e6769-114">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="e6769-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6769-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6769-115">See also</span></span>

- [<span data-ttu-id="e6769-116">SetNotifyFilter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6769-116">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="e6769-117">Tanılama Sembol Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="e6769-117">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
