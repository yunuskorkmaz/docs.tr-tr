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
ms.openlocfilehash: 93e96d6f8570e6aef7bfc18ef2859dc1e86ec8fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429037"
---
# <a name="userthread-structure"></a><span data-ttu-id="fd504-102">USER_THREAD Yapısı</span><span class="sxs-lookup"><span data-stu-id="fd504-102">USER_THREAD Structure</span></span>
<span data-ttu-id="fd504-103">Hata ayıklayıcı bir iş parçacığı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd504-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="fd504-104">Daha fazla bilgi için bkz: [Inotifysource2::setnotifyfilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fd504-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd504-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd504-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="fd504-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fd504-106">Members</span></span>  
  
|<span data-ttu-id="fd504-107">Üye</span><span class="sxs-lookup"><span data-stu-id="fd504-107">Member</span></span>|<span data-ttu-id="fd504-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd504-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="fd504-109">İş parçacığı arabellek adresi.</span><span class="sxs-lookup"><span data-stu-id="fd504-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="fd504-110">İş parçacığı arabelleğinin bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="fd504-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="fd504-111">İş parçacığı kimliği</span><span class="sxs-lookup"><span data-stu-id="fd504-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd504-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd504-112">Requirements</span></span>  
 <span data-ttu-id="fd504-113">**Başlık:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="fd504-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd504-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd504-114">See Also</span></span>  
 [<span data-ttu-id="fd504-115">SetNotifyFilter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd504-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)  
 [<span data-ttu-id="fd504-116">Tanılama Simge Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="fd504-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
