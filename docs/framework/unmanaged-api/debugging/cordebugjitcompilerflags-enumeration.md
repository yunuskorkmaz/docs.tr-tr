---
description: 'Daha fazla bilgi edinin: CorDebugJITCompilerFlags numaralandırması'
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
ms.openlocfilehash: 7e5337293aa4fe446deb12653acd22864eb7679a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801611"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="a638a-103">CorDebugJITCompilerFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a638a-103">CorDebugJITCompilerFlags Enumeration</span></span>

<span data-ttu-id="a638a-104">Yönetilen Just-In-Time (JıT) derleyicisinin davranışını etkileyen değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="a638a-104">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a638a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a638a-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a638a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a638a-106">Members</span></span>  
  
|<span data-ttu-id="a638a-107">Üye</span><span class="sxs-lookup"><span data-stu-id="a638a-107">Member</span></span>|<span data-ttu-id="a638a-108">Description</span><span class="sxs-lookup"><span data-stu-id="a638a-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="a638a-109">Derleyicinin derleme verilerini izlemesi gerektiğini ve iyileştirmelere izin verdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a638a-109">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="a638a-110">Derleyicinin derleme verilerini izlemesi gerektiğini, ancak iyileştirmeleri devre dışı bıraktığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a638a-110">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="a638a-111">Derleyicinin derleme verilerini izlemesi gerektiğini, iyileştirmeleri devre dışı bıraktığını ve düzenleme ve devam teknolojilerini kullanmasını gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a638a-111">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a638a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a638a-112">Requirements</span></span>  

 <span data-ttu-id="a638a-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a638a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a638a-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a638a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a638a-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a638a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a638a-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a638a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a638a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a638a-117">See also</span></span>

- [<span data-ttu-id="a638a-118">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="a638a-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
