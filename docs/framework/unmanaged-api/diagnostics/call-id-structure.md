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
ms.openlocfilehash: 8c606f67766334800444f39b115d90f65ecca13d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448586"
---
# <a name="call_id-structure"></a><span data-ttu-id="3c1a7-102">CALL_ID Yapısı</span><span class="sxs-lookup"><span data-stu-id="3c1a7-102">CALL_ID Structure</span></span>
<span data-ttu-id="3c1a7-103">Çağrılmakta olan bir işlev hakkında bilgi bir hata ayıklayıcıyla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c1a7-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="3c1a7-104">Daha fazla bilgi için bkz. [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3c1a7-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c1a7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c1a7-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3c1a7-106">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="3c1a7-106">Members</span></span>  
  
|<span data-ttu-id="3c1a7-107">Üyesi</span><span class="sxs-lookup"><span data-stu-id="3c1a7-107">Member</span></span>|<span data-ttu-id="3c1a7-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c1a7-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="3c1a7-109">Çağrıyı yapan makineyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c1a7-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="3c1a7-110">Makine işlemcisini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c1a7-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="3c1a7-111">Çağrıyı yürüten iş parçacığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c1a7-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="3c1a7-112">Çağrı yığınının adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c1a7-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="3c1a7-113">Çağrının adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c1a7-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="3c1a7-114">Çağrıyı yürütecek makineyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c1a7-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c1a7-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c1a7-115">Requirements</span></span>  
 <span data-ttu-id="3c1a7-116">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="3c1a7-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c1a7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c1a7-117">See also</span></span>

- [<span data-ttu-id="3c1a7-118">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c1a7-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="3c1a7-119">Tanılama Simge Deposu Yapıları</span><span class="sxs-lookup"><span data-stu-id="3c1a7-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
