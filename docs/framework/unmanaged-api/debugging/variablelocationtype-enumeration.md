---
description: 'Daha fazla bilgi edinin: VariableLocationType numaralandırması'
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
ms.openlocfilehash: 8561077b9f3f4d318eeb743d51538b2a9a22a217
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800532"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="5ba06-103">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="5ba06-103">VariableLocationType Enumeration</span></span>

<span data-ttu-id="5ba06-104">Bir değişkenin yerel konum türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ba06-104">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ba06-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ba06-105">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="5ba06-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5ba06-106">Members</span></span>  
  
|<span data-ttu-id="5ba06-107">Üye</span><span class="sxs-lookup"><span data-stu-id="5ba06-107">Member</span></span>|<span data-ttu-id="5ba06-108">Description</span><span class="sxs-lookup"><span data-stu-id="5ba06-108">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="5ba06-109">Değişken bir yazmaç içinde.</span><span class="sxs-lookup"><span data-stu-id="5ba06-109">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="5ba06-110">Değişken, YAZMAÇ göreli bir bellek konumudur.</span><span class="sxs-lookup"><span data-stu-id="5ba06-110">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="5ba06-111">Değişken, YAZMAÇ veya yazmaç göreli bellek konumunda depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="5ba06-111">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ba06-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ba06-112">Remarks</span></span>  

 <span data-ttu-id="5ba06-113">Sabit listesinin bir üyesi `VariableLocationType` [ıcordebugvariablehome:: GetLocationType](icordebugvariablehome-getlocationtype-method.md) yöntemi tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5ba06-113">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ba06-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ba06-114">Requirements</span></span>  

 <span data-ttu-id="5ba06-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ba06-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ba06-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5ba06-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ba06-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5ba06-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ba06-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ba06-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ba06-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ba06-119">See also</span></span>

- [<span data-ttu-id="5ba06-120">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="5ba06-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
