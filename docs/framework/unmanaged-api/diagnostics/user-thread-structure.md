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
ms.openlocfilehash: 409651aa69e957418ad46f61e1bd57add0eb10a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722901"
---
# <a name="user_thread-structure"></a><span data-ttu-id="93cb4-102">USER_THREAD Yapısı</span><span class="sxs-lookup"><span data-stu-id="93cb4-102">USER_THREAD Structure</span></span>

<span data-ttu-id="93cb4-103">Bir iş parçacığı hakkındaki hata ayıklayıcıyla ilgili bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="93cb4-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="93cb4-104">Daha fazla bilgi için bkz. [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="93cb4-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93cb4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="93cb4-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="93cb4-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="93cb4-106">Members</span></span>  
  
|<span data-ttu-id="93cb4-107">Üye</span><span class="sxs-lookup"><span data-stu-id="93cb4-107">Member</span></span>|<span data-ttu-id="93cb4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93cb4-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="93cb4-109">İş parçacığı arabelleğinin adresi.</span><span class="sxs-lookup"><span data-stu-id="93cb4-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="93cb4-110">İş parçacığı arabelleğinin bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="93cb4-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="93cb4-111">İş parçacığı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="93cb4-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93cb4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93cb4-112">Requirements</span></span>  

 <span data-ttu-id="93cb4-113">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="93cb4-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93cb4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93cb4-114">See also</span></span>

- [<span data-ttu-id="93cb4-115">SetNotifyFilter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93cb4-115">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="93cb4-116">Tanılama Sembol Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="93cb4-116">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
