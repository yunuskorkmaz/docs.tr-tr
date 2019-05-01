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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986524"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="a823f-102">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a823f-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="a823f-103">Bir değişken yerel konum türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a823f-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a823f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a823f-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="a823f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a823f-105">Members</span></span>  
  
|<span data-ttu-id="a823f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a823f-106">Member</span></span>|<span data-ttu-id="a823f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a823f-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="a823f-108">Bir kayıttaki değişkendir.</span><span class="sxs-lookup"><span data-stu-id="a823f-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="a823f-109">Register-göreli bellek konumunda değişkendir.</span><span class="sxs-lookup"><span data-stu-id="a823f-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="a823f-110">Değişken, bir kayıt veya bir kayıt göreli bellek konumuna depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="a823f-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a823f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a823f-111">Remarks</span></span>  
 <span data-ttu-id="a823f-112">Üye `VariableLocationType` numaralandırması tarafından döndürülen [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a823f-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a823f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a823f-113">Requirements</span></span>  
 <span data-ttu-id="a823f-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a823f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a823f-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a823f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a823f-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a823f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a823f-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a823f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a823f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a823f-118">See also</span></span>

- [<span data-ttu-id="a823f-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a823f-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
