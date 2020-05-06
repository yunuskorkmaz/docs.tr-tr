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
ms.openlocfilehash: 7b8a726cffcc00d7371675192a209b2d8e9db94d
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795787"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="d4ffd-102">CorDebugJITCompilerFlagsDeprecated Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d4ffd-102">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>
<span data-ttu-id="d4ffd-103">Bu numaralandırma artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d4ffd-103">This enumeration is obsolete.</span></span> <span data-ttu-id="d4ffd-104">Bunun yerine `CORDEBUG_JIT_DEFAULT` [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırmasının üyesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4ffd-104">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4ffd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4ffd-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="d4ffd-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d4ffd-106">Members</span></span>  
  
|<span data-ttu-id="d4ffd-107">Üye</span><span class="sxs-lookup"><span data-stu-id="d4ffd-107">Member</span></span>|<span data-ttu-id="d4ffd-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4ffd-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="d4ffd-109">Bunun yerine `CORDEBUG_JIT_DEFAULT` kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4ffd-109">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d4ffd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4ffd-110">Requirements</span></span>  
 <span data-ttu-id="d4ffd-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4ffd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4ffd-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d4ffd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4ffd-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d4ffd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4ffd-114">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="d4ffd-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ffd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4ffd-115">See also</span></span>

- [<span data-ttu-id="d4ffd-116">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="d4ffd-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
