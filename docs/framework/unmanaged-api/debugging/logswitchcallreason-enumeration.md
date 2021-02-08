---
description: 'Daha fazla bilgi edinin: LogSwitchCallReason numaralandırması'
title: LogSwitchCallReason Numaralandırması
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
ms.openlocfilehash: 46c457ee4c12fe9a73796aa7b7a5f599d90c9c6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800621"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="d44d4-103">LogSwitchCallReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d44d4-103">LogSwitchCallReason Enumeration</span></span>

<span data-ttu-id="d44d4-104">Hata ayıklama/izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d44d4-104">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d44d4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d44d4-105">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="d44d4-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d44d4-106">Members</span></span>  
  
|<span data-ttu-id="d44d4-107">Üye</span><span class="sxs-lookup"><span data-stu-id="d44d4-107">Member</span></span>|<span data-ttu-id="d44d4-108">Description</span><span class="sxs-lookup"><span data-stu-id="d44d4-108">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="d44d4-109">Hata ayıklama/izleme anahtarı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="d44d4-109">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="d44d4-110">Bir hata ayıklama/izleme anahtarı değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="d44d4-110">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="d44d4-111">Hata ayıklama/izleme anahtarı silindi.</span><span class="sxs-lookup"><span data-stu-id="d44d4-111">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d44d4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d44d4-112">Requirements</span></span>  

 <span data-ttu-id="d44d4-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d44d4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d44d4-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d44d4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d44d4-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d44d4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d44d4-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d44d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d44d4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d44d4-117">See also</span></span>

- [<span data-ttu-id="d44d4-118">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="d44d4-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
