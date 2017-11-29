---
title: "USER_THREAD Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: USER_THREAD
api_location: diasymreader.dll
api_type: COM
f1_keywords: USER_THREAD
helpviewer_keywords: USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d93002fe5460bfdb36d4e11c74410677b46a98d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="userthread-structure"></a><span data-ttu-id="9a043-102">USER_THREAD Yapısı</span><span class="sxs-lookup"><span data-stu-id="9a043-102">USER_THREAD Structure</span></span>
<span data-ttu-id="9a043-103">Hata ayıklayıcı bir iş parçacığı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a043-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="9a043-104">Daha fazla bilgi için bkz: [Inotifysource2::setnotifyfilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a043-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a043-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a043-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="9a043-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9a043-106">Members</span></span>  
  
|<span data-ttu-id="9a043-107">Üye</span><span class="sxs-lookup"><span data-stu-id="9a043-107">Member</span></span>|<span data-ttu-id="9a043-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a043-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="9a043-109">İş parçacığı arabellek adresi.</span><span class="sxs-lookup"><span data-stu-id="9a043-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="9a043-110">İş parçacığı arabelleğinin bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="9a043-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="9a043-111">İş parçacığı kimliği</span><span class="sxs-lookup"><span data-stu-id="9a043-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a043-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a043-112">Requirements</span></span>  
 <span data-ttu-id="9a043-113">**Başlık:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="9a043-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a043-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a043-114">See Also</span></span>  
 [<span data-ttu-id="9a043-115">SetNotifyFilter yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a043-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)  
 [<span data-ttu-id="9a043-116">Tanılama sembol deposu yapıları</span><span class="sxs-lookup"><span data-stu-id="9a043-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
