---
title: "CorDebugJITCompilerFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugJITCompilerFlags
helpviewer_keywords: CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfb78a160a7a6b9f50174fc8bb177cfd8d3f9383
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="cb0af-102">CorDebugJITCompilerFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cb0af-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="cb0af-103">Yönetilen tam zamanında (JIT) derleyici davranışını etkilemek değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cb0af-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb0af-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb0af-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="cb0af-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cb0af-105">Members</span></span>  
  
|<span data-ttu-id="cb0af-106">Üye</span><span class="sxs-lookup"><span data-stu-id="cb0af-106">Member</span></span>|<span data-ttu-id="cb0af-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb0af-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="cb0af-108">Derleyici derleme verileri izlemek ve iyileştirmeler sağlar belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb0af-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="cb0af-109">Derleyici devre dışı bırakır iyileştirmeler ancak derleme verileri izlemek belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb0af-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="cb0af-110">Derleme verileri, devre dışı bırakır iyileştirmeler derleyici izlemek ve etkinleştirir Düzenle ve devam teknolojileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb0af-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb0af-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb0af-111">Requirements</span></span>  
 <span data-ttu-id="cb0af-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb0af-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb0af-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb0af-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb0af-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb0af-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb0af-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb0af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb0af-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb0af-116">See Also</span></span>  
 [<span data-ttu-id="cb0af-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="cb0af-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
