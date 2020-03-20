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
ms.openlocfilehash: e2fa5d5a998f51e0e90cfde22b40ec12f278307b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178358"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="2a921-102">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2a921-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="2a921-103">Bir değişkenin yerel konum türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a921-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a921-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a921-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="2a921-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2a921-105">Members</span></span>  
  
|<span data-ttu-id="2a921-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2a921-106">Member</span></span>|<span data-ttu-id="2a921-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a921-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="2a921-108">Değişken bir kayıtta.</span><span class="sxs-lookup"><span data-stu-id="2a921-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="2a921-109">Değişken, kayıt bağıyla göreli bellek konumundadır.</span><span class="sxs-lookup"><span data-stu-id="2a921-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="2a921-110">Değişken bir kayıt ta veya bir kayıt göreli bellek konumunda depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="2a921-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a921-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a921-111">Remarks</span></span>  
 <span data-ttu-id="2a921-112">Numaralandırmanın `VariableLocationType` bir üyesi [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) yöntemi ile döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2a921-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a921-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a921-113">Requirements</span></span>  
 <span data-ttu-id="2a921-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a921-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a921-115">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a921-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a921-116">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a921-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a921-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a921-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a921-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a921-118">See also</span></span>

- [<span data-ttu-id="2a921-119">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="2a921-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
