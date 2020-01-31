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
ms.openlocfilehash: 39b90ba35510a5eda7b34e0a80b0e889e5804ca7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778225"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="7bd79-102">CorDebugJITCompilerFlagsDeprecated Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7bd79-102">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>
<span data-ttu-id="7bd79-103">Bu numaralandırma artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="7bd79-103">This enumeration is obsolete.</span></span> <span data-ttu-id="7bd79-104">Bunun yerine [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırmasının `CORDEBUG_JIT_DEFAULT` üyesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7bd79-104">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bd79-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bd79-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="7bd79-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7bd79-106">Members</span></span>  
  
|<span data-ttu-id="7bd79-107">Üye</span><span class="sxs-lookup"><span data-stu-id="7bd79-107">Member</span></span>|<span data-ttu-id="7bd79-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bd79-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="7bd79-109">Bunun yerine `CORDEBUG_JIT_DEFAULT` kullanın.</span><span class="sxs-lookup"><span data-stu-id="7bd79-109">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7bd79-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bd79-110">Requirements</span></span>  
 <span data-ttu-id="7bd79-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bd79-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bd79-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7bd79-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bd79-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7bd79-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bd79-114">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="7bd79-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd79-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bd79-115">See also</span></span>

- [<span data-ttu-id="7bd79-116">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7bd79-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
