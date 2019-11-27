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
ms.openlocfilehash: 51db7a2b6464b562e09ce061991898a8d604ead1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437972"
---
# <a name="user_thread-structure"></a><span data-ttu-id="e27ce-102">USER_THREAD Yapısı</span><span class="sxs-lookup"><span data-stu-id="e27ce-102">USER_THREAD Structure</span></span>
<span data-ttu-id="e27ce-103">Bir iş parçacığı hakkındaki hata ayıklayıcıyla ilgili bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e27ce-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="e27ce-104">Daha fazla bilgi için bkz. [INotifySource2:: SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e27ce-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e27ce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e27ce-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="e27ce-106">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="e27ce-106">Members</span></span>  
  
|<span data-ttu-id="e27ce-107">Üyesi</span><span class="sxs-lookup"><span data-stu-id="e27ce-107">Member</span></span>|<span data-ttu-id="e27ce-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e27ce-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="e27ce-109">İş parçacığı arabelleğinin adresi.</span><span class="sxs-lookup"><span data-stu-id="e27ce-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="e27ce-110">İş parçacığı arabelleğinin bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="e27ce-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="e27ce-111">İş parçacığı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e27ce-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e27ce-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e27ce-112">Requirements</span></span>  
 <span data-ttu-id="e27ce-113">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="e27ce-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e27ce-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e27ce-114">See also</span></span>

- [<span data-ttu-id="e27ce-115">SetNotifyFilter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e27ce-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="e27ce-116">Tanılama Simge Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="e27ce-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
