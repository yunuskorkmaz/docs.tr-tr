---
title: CALL_ID Yapısı
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6fa729b131d12b2825a2def700fd918ce8acc40
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220181"
---
# <a name="callid-structure"></a><span data-ttu-id="7a3f0-102">CALL_ID Yapısı</span><span class="sxs-lookup"><span data-stu-id="7a3f0-102">CALL_ID Structure</span></span>
<span data-ttu-id="7a3f0-103">Bir hata ayıklayıcı çağrılan bir işlev hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a3f0-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="7a3f0-104">Bkz: [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) daha fazla bilgi için arabirim.</span><span class="sxs-lookup"><span data-stu-id="7a3f0-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a3f0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a3f0-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="7a3f0-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7a3f0-106">Members</span></span>  
  
|<span data-ttu-id="7a3f0-107">Üye</span><span class="sxs-lookup"><span data-stu-id="7a3f0-107">Member</span></span>|<span data-ttu-id="7a3f0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a3f0-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="7a3f0-109">Çağrıyı yapan makineyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7a3f0-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="7a3f0-110">Makine işlemci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7a3f0-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="7a3f0-111">Çağrıyı yürütmeden iş parçacığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7a3f0-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="7a3f0-112">Çağrı yığınının adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a3f0-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="7a3f0-113">Çağrı adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a3f0-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="7a3f0-114">Çağrı yürütecek makineyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7a3f0-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a3f0-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a3f0-115">Requirements</span></span>  
 <span data-ttu-id="7a3f0-116">**Üst bilgi:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="7a3f0-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a3f0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a3f0-117">See also</span></span>

- [<span data-ttu-id="7a3f0-118">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a3f0-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="7a3f0-119">Tanılama Sembol Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="7a3f0-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
