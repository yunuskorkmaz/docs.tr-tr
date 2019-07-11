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
ms.openlocfilehash: 2093466c78b039a06a01e2d850b88ff4543d0ab3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752460"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="206da-102">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="206da-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="206da-103">Bir değişken yerel konum türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="206da-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="206da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="206da-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="206da-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="206da-105">Members</span></span>  
  
|<span data-ttu-id="206da-106">Üye</span><span class="sxs-lookup"><span data-stu-id="206da-106">Member</span></span>|<span data-ttu-id="206da-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="206da-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="206da-108">Bir kayıttaki değişkendir.</span><span class="sxs-lookup"><span data-stu-id="206da-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="206da-109">Register-göreli bellek konumunda değişkendir.</span><span class="sxs-lookup"><span data-stu-id="206da-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="206da-110">Değişken, bir kayıt veya bir kayıt göreli bellek konumuna depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="206da-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="206da-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="206da-111">Remarks</span></span>  
 <span data-ttu-id="206da-112">Üye `VariableLocationType` numaralandırması tarafından döndürülen [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="206da-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="206da-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="206da-113">Requirements</span></span>  
 <span data-ttu-id="206da-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="206da-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="206da-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="206da-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="206da-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="206da-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="206da-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="206da-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="206da-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="206da-118">See also</span></span>

- [<span data-ttu-id="206da-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="206da-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
