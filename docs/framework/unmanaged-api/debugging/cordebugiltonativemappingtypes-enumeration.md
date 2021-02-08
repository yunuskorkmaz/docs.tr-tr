---
description: ': CorDebugIlToNativeMappingTypes numaralandırması hakkında daha fazla bilgi'
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
ms.openlocfilehash: bcca11bf3c7574fe76684f6786d7408c80acfa43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801641"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="cb465-103">CorDebugIlToNativeMappingTypes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cb465-103">CorDebugIlToNativeMappingTypes Enumeration</span></span>

<span data-ttu-id="cb465-104">COR_DEBUG_IL_TO_NATIVE_MAP yapısının bir örneğiyle temsil edilen belirli bir yerel yönerge aralığının özel bir kod bölgesine karşılık geldiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb465-104">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb465-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cb465-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="cb465-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cb465-106">Members</span></span>  
  
|<span data-ttu-id="cb465-107">Üye</span><span class="sxs-lookup"><span data-stu-id="cb465-107">Member</span></span>|<span data-ttu-id="cb465-108">Description</span><span class="sxs-lookup"><span data-stu-id="cb465-108">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="cb465-109">Yerel yönergelerin aralığı herhangi bir özel kod bölgesine karşılık gelmiyor.</span><span class="sxs-lookup"><span data-stu-id="cb465-109">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="cb465-110">Yerel yönergelerin aralığı giriş alanına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="cb465-110">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="cb465-111">Yerel yönergelerin aralığı, bitiş değerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="cb465-111">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb465-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb465-112">Requirements</span></span>  

 <span data-ttu-id="cb465-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb465-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb465-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cb465-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb465-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cb465-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb465-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb465-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb465-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb465-117">See also</span></span>

- [<span data-ttu-id="cb465-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb465-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="cb465-119">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="cb465-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
