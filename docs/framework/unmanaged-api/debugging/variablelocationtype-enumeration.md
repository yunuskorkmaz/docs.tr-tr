---
title: VariableLocationType Sabit Listesi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 392254efcd099aca60e58b3cc0bc61ca85aa2c66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099956"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="f62ac-102">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f62ac-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="f62ac-103">Bir değişken yerel konum türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f62ac-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f62ac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f62ac-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="f62ac-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f62ac-105">Members</span></span>  
  
|<span data-ttu-id="f62ac-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f62ac-106">Member</span></span>|<span data-ttu-id="f62ac-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f62ac-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="f62ac-108">Bir kayıttaki değişkendir.</span><span class="sxs-lookup"><span data-stu-id="f62ac-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="f62ac-109">Register-göreli bellek konumunda değişkendir.</span><span class="sxs-lookup"><span data-stu-id="f62ac-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="f62ac-110">Değişken, bir kayıt veya bir kayıt göreli bellek konumuna depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="f62ac-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f62ac-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f62ac-111">Remarks</span></span>  
 <span data-ttu-id="f62ac-112">Üye `VariableLocationType` numaralandırması tarafından döndürülen [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f62ac-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f62ac-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f62ac-113">Requirements</span></span>  
 <span data-ttu-id="f62ac-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f62ac-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f62ac-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f62ac-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f62ac-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f62ac-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f62ac-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f62ac-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f62ac-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f62ac-118">See also</span></span>

- [<span data-ttu-id="f62ac-119">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f62ac-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
