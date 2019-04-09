---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae3ba480e208762f5a80f9f1b78dd008f02b6df4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089388"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="d3759-102">CorDebugCreateProcessFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d3759-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="d3759-103">Bir çağrıda kullanılan ek hata ayıklama seçenekleri sağlar [Icordebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d3759-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3759-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3759-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d3759-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d3759-105">Members</span></span>  
  
|<span data-ttu-id="d3759-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d3759-106">Member</span></span>|<span data-ttu-id="d3759-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3759-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="d3759-108">Özel seçeneği ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d3759-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3759-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3759-109">Requirements</span></span>  
 <span data-ttu-id="d3759-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3759-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3759-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3759-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3759-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3759-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d3759-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d3759-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d3759-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3759-114">See also</span></span>

- [<span data-ttu-id="d3759-115">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="d3759-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
