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
# <a name="user_thread-structure"></a><span data-ttu-id="0b248-102">USER_THREAD Yapısı</span><span class="sxs-lookup"><span data-stu-id="0b248-102">USER_THREAD Structure</span></span>
<span data-ttu-id="0b248-103">Provides information to a debugger about a thread.</span><span class="sxs-lookup"><span data-stu-id="0b248-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="0b248-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="0b248-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b248-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b248-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="0b248-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0b248-106">Members</span></span>  
  
|<span data-ttu-id="0b248-107">Üye</span><span class="sxs-lookup"><span data-stu-id="0b248-107">Member</span></span>|<span data-ttu-id="0b248-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b248-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="0b248-109">Address of thread buffer.</span><span class="sxs-lookup"><span data-stu-id="0b248-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="0b248-110">Length of thread buffer, in bytes.</span><span class="sxs-lookup"><span data-stu-id="0b248-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="0b248-111">Thread ID.</span><span class="sxs-lookup"><span data-stu-id="0b248-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b248-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b248-112">Requirements</span></span>  
 <span data-ttu-id="0b248-113">**Header:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="0b248-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b248-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b248-114">See also</span></span>

- [<span data-ttu-id="0b248-115">SetNotifyFilter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b248-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="0b248-116">Tanılama Simge Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="0b248-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
