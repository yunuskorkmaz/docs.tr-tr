---
title: CorDebugJITCompilerFlagsDeprecated Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlagsDeprecated
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlagsDeprecated
helpviewer_keywords:
- CorDebugJITCompilerFlagsDeprecated enumeration [.NET Framework debugging]
ms.assetid: af15e2ca-6be1-472b-bd36-03644a1e3ddd
topic_type:
- apiref
ms.openlocfilehash: d731b12ddf195137ff38d32ab0ca52aa90f48d4e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132781"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="f712e-102">CorDebugJITCompilerFlagsDeprecated Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f712e-102">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>
<span data-ttu-id="f712e-103">Bu numaralandırma artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="f712e-103">This enumeration is obsolete.</span></span> <span data-ttu-id="f712e-104">Bunun yerine [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırmasının `CORDEBUG_JIT_DEFAULT` üyesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f712e-104">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f712e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f712e-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="f712e-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f712e-106">Members</span></span>  
  
|<span data-ttu-id="f712e-107">Üye</span><span class="sxs-lookup"><span data-stu-id="f712e-107">Member</span></span>|<span data-ttu-id="f712e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f712e-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="f712e-109">Bunun yerine `CORDEBUG_JIT_DEFAULT` kullanın.</span><span class="sxs-lookup"><span data-stu-id="f712e-109">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f712e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f712e-110">Requirements</span></span>  
 <span data-ttu-id="f712e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f712e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f712e-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f712e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f712e-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f712e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f712e-114">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="f712e-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f712e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f712e-115">See also</span></span>

- [<span data-ttu-id="f712e-116">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f712e-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
