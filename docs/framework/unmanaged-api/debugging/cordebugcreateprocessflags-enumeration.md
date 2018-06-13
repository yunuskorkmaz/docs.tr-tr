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
ms.openlocfilehash: 9fdc37676bfae8ac90fde0a7a5b11037b8357e25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403763"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="2e01d-102">CorDebugCreateProcessFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2e01d-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="2e01d-103">Çağrıda kullanılan ek hata ayıklama seçenekleri sunar [Icordebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2e01d-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e01d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e01d-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2e01d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2e01d-105">Members</span></span>  
  
|<span data-ttu-id="2e01d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2e01d-106">Member</span></span>|<span data-ttu-id="2e01d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e01d-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="2e01d-108">Hiçbir özel seçeneklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2e01d-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2e01d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e01d-109">Requirements</span></span>  
 <span data-ttu-id="2e01d-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e01d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e01d-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e01d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e01d-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e01d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e01d-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e01d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e01d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e01d-114">See Also</span></span>  
 [<span data-ttu-id="2e01d-115">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="2e01d-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
