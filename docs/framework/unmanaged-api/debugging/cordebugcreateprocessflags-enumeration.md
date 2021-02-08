---
description: 'Bu konuda daha fazla bilgi edinin: CorDebugCreateProcessFlags numaralandırması'
title: CorDebugCreateProcessFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
ms.openlocfilehash: 29363510c83873c7f367079857809c165bc55b1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801741"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="7109e-103">CorDebugCreateProcessFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7109e-103">CorDebugCreateProcessFlags Enumeration</span></span>

<span data-ttu-id="7109e-104">[ICorDebug:: CreateProcess](icordebug-createprocess-method.md) metoduna yapılan bir çağrıda kullanılabilecek ek hata ayıklama seçenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7109e-104">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7109e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7109e-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="7109e-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7109e-106">Members</span></span>  
  
|<span data-ttu-id="7109e-107">Üye</span><span class="sxs-lookup"><span data-stu-id="7109e-107">Member</span></span>|<span data-ttu-id="7109e-108">Description</span><span class="sxs-lookup"><span data-stu-id="7109e-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="7109e-109">Hiçbir özel seçenek ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="7109e-109">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7109e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7109e-110">Requirements</span></span>  

 <span data-ttu-id="7109e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7109e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7109e-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7109e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7109e-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7109e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7109e-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7109e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7109e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7109e-115">See also</span></span>

- [<span data-ttu-id="7109e-116">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="7109e-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
