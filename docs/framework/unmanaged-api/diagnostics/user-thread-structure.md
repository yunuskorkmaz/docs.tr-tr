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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acc4da79796e975d349d1cb33c301c25c4791cb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709084"
---
# <a name="userthread-structure"></a><span data-ttu-id="b20f0-102">USER_THREAD Yapısı</span><span class="sxs-lookup"><span data-stu-id="b20f0-102">USER_THREAD Structure</span></span>
<span data-ttu-id="b20f0-103">Bir hata ayıklayıcı bir iş parçacığı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b20f0-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="b20f0-104">Daha fazla bilgi için [Inotifysource2::setnotifyfilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b20f0-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b20f0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b20f0-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="b20f0-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b20f0-106">Members</span></span>  
  
|<span data-ttu-id="b20f0-107">Üye</span><span class="sxs-lookup"><span data-stu-id="b20f0-107">Member</span></span>|<span data-ttu-id="b20f0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b20f0-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="b20f0-109">İş parçacığı arabellek adresi.</span><span class="sxs-lookup"><span data-stu-id="b20f0-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="b20f0-110">İş parçacığı arabelleğin bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="b20f0-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="b20f0-111">İş parçacığı kimliği</span><span class="sxs-lookup"><span data-stu-id="b20f0-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b20f0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b20f0-112">Requirements</span></span>  
 <span data-ttu-id="b20f0-113">**Üst bilgi:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="b20f0-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b20f0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b20f0-114">See also</span></span>
- [<span data-ttu-id="b20f0-115">SetNotifyFilter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b20f0-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="b20f0-116">Tanılama Simge Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="b20f0-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
