---
title: CorDebugMappingResult Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
ms.openlocfilehash: fc3f77adf33502bfbc3d65ff5131420093fbbec8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097932"
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="fe741-102">CorDebugMappingResult Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fe741-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="fe741-103">Yönerge işaretçisinin (IP) değerinin nasıl alındıklarına ilişkin ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe741-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe741-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe741-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="fe741-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fe741-105">Members</span></span>  
  
|<span data-ttu-id="fe741-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fe741-106">Member</span></span>|<span data-ttu-id="fe741-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe741-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="fe741-108">Yerel kod giriş durumunda olduğundan IP değeri 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="fe741-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="fe741-109">Yerel kod bir bitişdir, bu nedenle IP değeri yöntemin son yönergesinin adresidir.</span><span class="sxs-lookup"><span data-stu-id="fe741-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="fe741-110">Yöntemi için hiçbir eşleme bilgisi yok, bu nedenle IP değeri 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="fe741-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="fe741-111">Yöntemi için eşleme bilgileri olsa da, geçerli adres Microsoft ara dili (MSIL) koduna eşlenemez.</span><span class="sxs-lookup"><span data-stu-id="fe741-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="fe741-112">IP değeri 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="fe741-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="fe741-113">Yöntemi tamamen MSIL koduna eşlenir veya çerçeve yorumlanmış olduğundan, IP değeri doğru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe741-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="fe741-114">Yöntem başarıyla eşlendi, ancak IP 'nin değeri yaklaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe741-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe741-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe741-115">Remarks</span></span>  
 <span data-ttu-id="fe741-116">Yönerge işaretçisinin değerini elde etmek için [ICorDebugILFrame:: GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe741-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe741-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe741-117">Requirements</span></span>  
 <span data-ttu-id="fe741-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe741-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe741-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fe741-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe741-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fe741-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe741-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe741-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe741-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe741-122">See also</span></span>

- [<span data-ttu-id="fe741-123">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fe741-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
