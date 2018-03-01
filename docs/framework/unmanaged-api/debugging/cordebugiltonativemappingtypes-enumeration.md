---
title: "CorDebugIlToNativeMappingTypes Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 44546c8d66eff111b70673ed63ab82d30fea0b6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="7a305-102">CorDebugIlToNativeMappingTypes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7a305-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="7a305-103">Cor_debug_ıl_to_natıve_map yapısı bir örneği tarafından temsil edilen yerel yönergeleri, belirli bir dizi özel kod bölgesine karşılık gelen olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a305-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a305-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a305-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="7a305-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7a305-105">Members</span></span>  
  
|<span data-ttu-id="7a305-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7a305-106">Member</span></span>|<span data-ttu-id="7a305-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a305-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="7a305-108">Yerel yönergeleri aralığını herhangi bir özel kod bölgeyi karşılık gelmiyor.</span><span class="sxs-lookup"><span data-stu-id="7a305-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="7a305-109">Yerel yönergeleri aralığını giriş karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="7a305-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="7a305-110">Yerel yönergeleri aralığı bitiş karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="7a305-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a305-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a305-111">Requirements</span></span>  
 <span data-ttu-id="7a305-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a305-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a305-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a305-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a305-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a305-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a305-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a305-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a305-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a305-116">See Also</span></span>  
 [<span data-ttu-id="7a305-117">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a305-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [<span data-ttu-id="7a305-118">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7a305-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
