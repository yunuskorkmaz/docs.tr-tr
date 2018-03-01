---
title: "CALL_ID Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 71fd69cbcced1440839b9eedf8fbe3d8f5b90646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="callid-structure"></a><span data-ttu-id="713a0-102">CALL_ID Yapısı</span><span class="sxs-lookup"><span data-stu-id="713a0-102">CALL_ID Structure</span></span>
<span data-ttu-id="713a0-103">Hata ayıklayıcı çağrıldığından işlevi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="713a0-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="713a0-104">Bkz: [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) daha fazla bilgi için arabirim.</span><span class="sxs-lookup"><span data-stu-id="713a0-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="713a0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="713a0-105">Syntax</span></span>  
  
```  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a><span data-ttu-id="713a0-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="713a0-106">Members</span></span>  
  
|<span data-ttu-id="713a0-107">Üye</span><span class="sxs-lookup"><span data-stu-id="713a0-107">Member</span></span>|<span data-ttu-id="713a0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="713a0-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="713a0-109">Çağrıyı yapan makineyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="713a0-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="713a0-110">Makine işlemci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="713a0-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="713a0-111">Çağrı yürütme iş parçacığı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="713a0-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="713a0-112">Çağrı yığını adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="713a0-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="713a0-113">Çağrı adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="713a0-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="713a0-114">Çağrı yürütecek makineyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="713a0-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="713a0-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="713a0-115">Requirements</span></span>  
 <span data-ttu-id="713a0-116">**Başlık:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="713a0-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713a0-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="713a0-117">See Also</span></span>  
 [<span data-ttu-id="713a0-118">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="713a0-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="713a0-119">Tanılama Simge Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="713a0-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
