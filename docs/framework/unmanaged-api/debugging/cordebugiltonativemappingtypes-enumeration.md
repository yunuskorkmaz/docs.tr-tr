---
title: "CorDebugIlToNativeMappingTypes Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugIlToNativeMappingTypes
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugIlToNativeMappingTypes
helpviewer_keywords: CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03046ebb678df64ad3d151aaadba313645417979
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="6a052-102">CorDebugIlToNativeMappingTypes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6a052-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="6a052-103">Cor_debug_ıl_to_natıve_map yapısı bir örneği tarafından temsil edilen yerel yönergeleri, belirli bir dizi özel kod bölgesine karşılık gelen olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a052-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a052-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a052-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="6a052-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6a052-105">Members</span></span>  
  
|<span data-ttu-id="6a052-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6a052-106">Member</span></span>|<span data-ttu-id="6a052-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a052-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="6a052-108">Yerel yönergeleri aralığını herhangi bir özel kod bölgeyi karşılık gelmiyor.</span><span class="sxs-lookup"><span data-stu-id="6a052-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="6a052-109">Yerel yönergeleri aralığını giriş karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="6a052-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="6a052-110">Yerel yönergeleri aralığı bitiş karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="6a052-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a052-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a052-111">Requirements</span></span>  
 <span data-ttu-id="6a052-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a052-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a052-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a052-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a052-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a052-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a052-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a052-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a052-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a052-116">See Also</span></span>  
 [<span data-ttu-id="6a052-117">Getıltonativemapping yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a052-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [<span data-ttu-id="6a052-118">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="6a052-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
