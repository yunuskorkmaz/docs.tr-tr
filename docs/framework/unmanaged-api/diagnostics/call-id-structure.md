---
description: 'Daha fazla bilgi edinin: CALL_ID yapısı'
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
ms.openlocfilehash: 4ef6023e382e8c5fead48494f428648a37f3bef4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800493"
---
# <a name="call_id-structure"></a><span data-ttu-id="ec587-103">CALL_ID Yapısı</span><span class="sxs-lookup"><span data-stu-id="ec587-103">CALL_ID Structure</span></span>

<span data-ttu-id="ec587-104">Çağrılmakta olan bir işlev hakkında bilgi bir hata ayıklayıcıyla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec587-104">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="ec587-105">Daha fazla bilgi için bkz. [INotifySink2](inotifysink2-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ec587-105">See the [INotifySink2](inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec587-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ec587-106">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="ec587-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ec587-107">Members</span></span>  
  
|<span data-ttu-id="ec587-108">Üye</span><span class="sxs-lookup"><span data-stu-id="ec587-108">Member</span></span>|<span data-ttu-id="ec587-109">Description</span><span class="sxs-lookup"><span data-stu-id="ec587-109">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="ec587-110">Çağrıyı yapan makineyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ec587-110">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="ec587-111">Makine işlemcisini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ec587-111">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="ec587-112">Çağrıyı yürüten iş parçacığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ec587-112">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="ec587-113">Çağrı yığınının adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec587-113">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="ec587-114">Çağrının adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec587-114">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="ec587-115">Çağrıyı yürütecek makineyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ec587-115">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec587-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec587-116">Requirements</span></span>  

 <span data-ttu-id="ec587-117">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="ec587-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec587-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec587-118">See also</span></span>

- [<span data-ttu-id="ec587-119">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec587-119">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="ec587-120">Tanılama Sembol Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="ec587-120">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
