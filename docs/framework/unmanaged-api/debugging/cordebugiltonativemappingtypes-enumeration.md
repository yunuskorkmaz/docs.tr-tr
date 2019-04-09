---
title: CorDebugIlToNativeMappingTypes Numaralandırması
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f62707fb1e52a96cf3f131e9c11fee82ab03f4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097193"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="f6bed-102">CorDebugIlToNativeMappingTypes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f6bed-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="f6bed-103">Cor_debug_ıl_to_natıve_map yapısı örneği tarafından temsil edilen yerel yönergeler, belirli bir dizi özel kod bölgesine karşılık gelen olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6bed-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6bed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6bed-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="f6bed-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f6bed-105">Members</span></span>  
  
|<span data-ttu-id="f6bed-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f6bed-106">Member</span></span>|<span data-ttu-id="f6bed-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6bed-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="f6bed-108">Yerel yönergeleri aralığını herhangi bir özel kod bölgesine karşılık gelmiyor.</span><span class="sxs-lookup"><span data-stu-id="f6bed-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="f6bed-109">Yerel yönergeleri aralığı için giriş karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f6bed-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="f6bed-110">Yerel yönergeleri aralığı için sonuç karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f6bed-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6bed-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6bed-111">Requirements</span></span>  
 <span data-ttu-id="f6bed-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6bed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6bed-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6bed-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6bed-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6bed-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f6bed-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f6bed-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f6bed-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6bed-116">See also</span></span>

- [<span data-ttu-id="f6bed-117">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6bed-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="f6bed-118">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f6bed-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
