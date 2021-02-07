---
description: 'Hakkında daha fazla bilgi edinin: CorDebugJITCompilerFlagsDeprecated numaralandırması'
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
ms.openlocfilehash: ac607766c484a63a757d726826c81d16edd48aae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661915"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="67abe-103">CorDebugJITCompilerFlagsDeprecated Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="67abe-103">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>

<span data-ttu-id="67abe-104">Bu numaralandırma artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="67abe-104">This enumeration is obsolete.</span></span> <span data-ttu-id="67abe-105">`CORDEBUG_JIT_DEFAULT`Bunun yerine [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırmasının üyesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="67abe-105">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67abe-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="67abe-106">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="67abe-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="67abe-107">Members</span></span>  
  
|<span data-ttu-id="67abe-108">Üye</span><span class="sxs-lookup"><span data-stu-id="67abe-108">Member</span></span>|<span data-ttu-id="67abe-109">Description</span><span class="sxs-lookup"><span data-stu-id="67abe-109">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="67abe-110">Bunun yerine `CORDEBUG_JIT_DEFAULT` kullanın.</span><span class="sxs-lookup"><span data-stu-id="67abe-110">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67abe-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67abe-111">Requirements</span></span>  

 <span data-ttu-id="67abe-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67abe-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67abe-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="67abe-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67abe-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="67abe-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67abe-115">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="67abe-115">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67abe-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67abe-116">See also</span></span>

- [<span data-ttu-id="67abe-117">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="67abe-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
