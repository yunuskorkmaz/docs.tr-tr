---
title: "VariableLocationType numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ea476ef32b807823108aa2836778da576618214
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="48571-102">VariableLocationType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="48571-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="48571-103">Bir değişken yerel konum türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="48571-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48571-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48571-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="48571-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="48571-105">Members</span></span>  
  
|<span data-ttu-id="48571-106">Üye</span><span class="sxs-lookup"><span data-stu-id="48571-106">Member</span></span>|<span data-ttu-id="48571-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48571-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="48571-108">Bir kayıttaki değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="48571-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="48571-109">Bir kayıt göreli bellek konumda değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="48571-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="48571-110">Değişken, bir kayıt veya bir kayıt göreli bellek konumundan depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="48571-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48571-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48571-111">Remarks</span></span>  
 <span data-ttu-id="48571-112">Üye `VariableLocationType` numaralandırması tarafından döndürülen [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="48571-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48571-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48571-113">Requirements</span></span>  
 <span data-ttu-id="48571-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48571-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48571-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48571-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48571-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48571-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48571-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48571-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48571-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48571-118">See Also</span></span>  
 [<span data-ttu-id="48571-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="48571-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
