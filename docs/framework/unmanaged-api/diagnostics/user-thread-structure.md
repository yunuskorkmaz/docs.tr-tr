---
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
ms.openlocfilehash: 5144feab742bc5dac36563d701d81a699d0bb2f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609449"
---
# <a name="user_thread-structure"></a><span data-ttu-id="5a0a1-102">USER_THREAD Yapısı</span><span class="sxs-lookup"><span data-stu-id="5a0a1-102">USER_THREAD Structure</span></span>
<span data-ttu-id="5a0a1-103">Bir iş parçacığı hakkındaki hata ayıklayıcıyla ilgili bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a0a1-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="5a0a1-104">Daha fazla bilgi için bkz. [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5a0a1-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a0a1-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5a0a1-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="5a0a1-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5a0a1-106">Members</span></span>  
  
|<span data-ttu-id="5a0a1-107">Üye</span><span class="sxs-lookup"><span data-stu-id="5a0a1-107">Member</span></span>|<span data-ttu-id="5a0a1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a0a1-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="5a0a1-109">İş parçacığı arabelleğinin adresi.</span><span class="sxs-lookup"><span data-stu-id="5a0a1-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="5a0a1-110">İş parçacığı arabelleğinin bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="5a0a1-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="5a0a1-111">İş parçacığı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="5a0a1-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a0a1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a0a1-112">Requirements</span></span>  
 <span data-ttu-id="5a0a1-113">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="5a0a1-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a0a1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a0a1-114">See also</span></span>

- [<span data-ttu-id="5a0a1-115">SetNotifyFilter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a0a1-115">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="5a0a1-116">Tanılama Sembol Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="5a0a1-116">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
