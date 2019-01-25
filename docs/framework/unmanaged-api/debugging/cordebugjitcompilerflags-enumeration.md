---
title: CorDebugJITCompilerFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 512122d264e0817b89e8a371f57f11d31f7c4380
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639654"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="9ef62-102">CorDebugJITCompilerFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9ef62-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="9ef62-103">Yönetilen just-ın-time (JIT) derleyici davranışını etkileyen değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="9ef62-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef62-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ef62-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="9ef62-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9ef62-105">Members</span></span>  
  
|<span data-ttu-id="9ef62-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9ef62-106">Member</span></span>|<span data-ttu-id="9ef62-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ef62-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="9ef62-108">Derleyici derleme veri izlemelisiniz ve iyileştirmelerini sağlar belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ef62-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="9ef62-109">Derleyici iyileştirmeleri devre dışı bırakır ancak derleme veri izleyeceğine belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ef62-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="9ef62-110">Derleyici iyileştirmeleri devre dışı bırakır, derleme veri izlemelisiniz ve Düzenle ve devam teknolojileri sağlar belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ef62-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ef62-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ef62-111">Requirements</span></span>  
 <span data-ttu-id="9ef62-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ef62-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ef62-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ef62-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ef62-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ef62-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ef62-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ef62-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef62-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ef62-116">See also</span></span>
- [<span data-ttu-id="9ef62-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="9ef62-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
