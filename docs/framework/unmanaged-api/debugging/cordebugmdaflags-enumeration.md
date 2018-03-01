---
title: "CorDebugMDAFlags Numaralandırması"
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
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: defd2572d6f925cf557539983308b3b3e900eebd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="7dd1f-102">CorDebugMDAFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7dd1f-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="7dd1f-103">İş parçacığı üzerinde yönetilen hata ayıklama Yardımcısı (MDA) tetiklenir durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7dd1f-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dd1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7dd1f-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="7dd1f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7dd1f-105">Members</span></span>  
  
|<span data-ttu-id="7dd1f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7dd1f-106">Member</span></span>|<span data-ttu-id="7dd1f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dd1f-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="7dd1f-108">MDA harekete beri MDA harekete iş parçacığı kaymış.</span><span class="sxs-lookup"><span data-stu-id="7dd1f-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dd1f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7dd1f-109">Remarks</span></span>  
 <span data-ttu-id="7dd1f-110">Çağrı yığını artık burada MDA başlangıçta gerçekleşmesine neden olan açıklar, iş parçacığı sahip olduğu kabul edildiği *kaymış*.</span><span class="sxs-lookup"><span data-stu-id="7dd1f-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="7dd1f-111">Bu, iş parçacığının yürütülmesi çıkarken geçersiz bir işlem tarafından duruma olağan dışı bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="7dd1f-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dd1f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7dd1f-112">Requirements</span></span>  
 <span data-ttu-id="7dd1f-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dd1f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dd1f-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7dd1f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7dd1f-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7dd1f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7dd1f-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dd1f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd1f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7dd1f-117">See Also</span></span>  
 [<span data-ttu-id="7dd1f-118">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7dd1f-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
