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
ms.openlocfilehash: ddb5af486ab6fb1c8c4fabf3ccf7b43d037e1eeb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789315"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="5e873-102">CorDebugIlToNativeMappingTypes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5e873-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="5e873-103">COR_DEBUG_IL_TO_NATIVE_MAP yapısının bir örneğiyle temsil edilen belirli bir yerel yönerge aralığının özel bir kod bölgesine karşılık geldiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e873-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e873-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e873-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="5e873-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5e873-105">Members</span></span>  
  
|<span data-ttu-id="5e873-106">Üye</span><span class="sxs-lookup"><span data-stu-id="5e873-106">Member</span></span>|<span data-ttu-id="5e873-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e873-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="5e873-108">Yerel yönergelerin aralığı herhangi bir özel kod bölgesine karşılık gelmiyor.</span><span class="sxs-lookup"><span data-stu-id="5e873-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="5e873-109">Yerel yönergelerin aralığı giriş alanına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="5e873-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="5e873-110">Yerel yönergelerin aralığı, bitiş değerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="5e873-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e873-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e873-111">Requirements</span></span>  
 <span data-ttu-id="5e873-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e873-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e873-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5e873-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e873-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5e873-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e873-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e873-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e873-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e873-116">See also</span></span>

- [<span data-ttu-id="5e873-117">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e873-117">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="5e873-118">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="5e873-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
