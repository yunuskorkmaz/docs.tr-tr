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
ms.openlocfilehash: 66a8ba59d221bb3fa2e815a1cbcfa79c474666cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105475"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="d96cc-102">CorDebugJITCompilerFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d96cc-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="d96cc-103">Yönetilen just-ın-time (JIT) derleyici davranışını etkileyen değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d96cc-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d96cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d96cc-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d96cc-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d96cc-105">Members</span></span>  
  
|<span data-ttu-id="d96cc-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d96cc-106">Member</span></span>|<span data-ttu-id="d96cc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d96cc-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="d96cc-108">Derleyici derleme veri izlemelisiniz ve iyileştirmelerini sağlar belirtir.</span><span class="sxs-lookup"><span data-stu-id="d96cc-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="d96cc-109">Derleyici iyileştirmeleri devre dışı bırakır ancak derleme veri izleyeceğine belirtir.</span><span class="sxs-lookup"><span data-stu-id="d96cc-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="d96cc-110">Derleyici iyileştirmeleri devre dışı bırakır, derleme veri izlemelisiniz ve Düzenle ve devam teknolojileri sağlar belirtir.</span><span class="sxs-lookup"><span data-stu-id="d96cc-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d96cc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d96cc-111">Requirements</span></span>  
 <span data-ttu-id="d96cc-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d96cc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d96cc-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d96cc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d96cc-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d96cc-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d96cc-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d96cc-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d96cc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d96cc-116">See also</span></span>

- [<span data-ttu-id="d96cc-117">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="d96cc-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
