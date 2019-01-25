---
title: VariableLocationType sabit listesi
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
ms.openlocfilehash: dd1a622faa095836a3d5c22c7a18084482074c2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653222"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="750e1-102">VariableLocationType sabit listesi</span><span class="sxs-lookup"><span data-stu-id="750e1-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="750e1-103">Bir değişken yerel konum türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="750e1-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="750e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="750e1-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="750e1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="750e1-105">Members</span></span>  
  
|<span data-ttu-id="750e1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="750e1-106">Member</span></span>|<span data-ttu-id="750e1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="750e1-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="750e1-108">Bir kayıttaki değişkendir.</span><span class="sxs-lookup"><span data-stu-id="750e1-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="750e1-109">Register-göreli bellek konumunda değişkendir.</span><span class="sxs-lookup"><span data-stu-id="750e1-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="750e1-110">Değişken, bir kayıt veya bir kayıt göreli bellek konumuna depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="750e1-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="750e1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="750e1-111">Remarks</span></span>  
 <span data-ttu-id="750e1-112">Üye `VariableLocationType` numaralandırması tarafından döndürülen [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="750e1-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="750e1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="750e1-113">Requirements</span></span>  
 <span data-ttu-id="750e1-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="750e1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="750e1-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="750e1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="750e1-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="750e1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="750e1-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="750e1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="750e1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="750e1-118">See also</span></span>
- [<span data-ttu-id="750e1-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="750e1-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
