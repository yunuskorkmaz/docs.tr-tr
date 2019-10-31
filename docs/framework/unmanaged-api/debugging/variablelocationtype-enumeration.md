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
ms.openlocfilehash: 861d5daa481132d3d6527e8d5fbccfab6436c5fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139113"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="6792b-102">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="6792b-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="6792b-103">Bir değişkenin yerel konum türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="6792b-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6792b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6792b-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="6792b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6792b-105">Members</span></span>  
  
|<span data-ttu-id="6792b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6792b-106">Member</span></span>|<span data-ttu-id="6792b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6792b-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="6792b-108">Değişken bir yazmaç içinde.</span><span class="sxs-lookup"><span data-stu-id="6792b-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="6792b-109">Değişken, YAZMAÇ göreli bir bellek konumudur.</span><span class="sxs-lookup"><span data-stu-id="6792b-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="6792b-110">Değişken, YAZMAÇ veya yazmaç göreli bellek konumunda depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="6792b-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6792b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6792b-111">Remarks</span></span>  
 <span data-ttu-id="6792b-112">`VariableLocationType` numaralandırmanın bir üyesi [ıcordebugvariablehome:: GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) yöntemi tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6792b-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6792b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6792b-113">Requirements</span></span>  
 <span data-ttu-id="6792b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6792b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6792b-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6792b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6792b-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6792b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6792b-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6792b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6792b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6792b-118">See also</span></span>

- [<span data-ttu-id="6792b-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6792b-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
