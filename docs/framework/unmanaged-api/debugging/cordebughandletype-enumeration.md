---
title: "CorDebugHandleType Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugHandleType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugHandleType
helpviewer_keywords: CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef0b892d8dc277286114e8f9eda8d0f16833e1d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="b2b76-102">CorDebugHandleType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b2b76-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="b2b76-103">Tanıtıcı türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2b76-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2b76-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2b76-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="b2b76-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b2b76-105">Members</span></span>  
  
|<span data-ttu-id="b2b76-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b2b76-106">Member</span></span>|<span data-ttu-id="b2b76-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2b76-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="b2b76-108">Atık toplama tarafından iadesi nesneyi önleyen güçlü, işleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="b2b76-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="b2b76-109">İşleyici, bir nesne atık toplama tarafından iadesi engellemez, zayıftır.</span><span class="sxs-lookup"><span data-stu-id="b2b76-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="b2b76-110">Nesne toplandığında tanıtıcı geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="b2b76-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2b76-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2b76-111">Requirements</span></span>  
 <span data-ttu-id="b2b76-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2b76-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2b76-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2b76-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2b76-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2b76-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2b76-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2b76-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b76-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2b76-116">See Also</span></span>  
 [<span data-ttu-id="b2b76-117">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="b2b76-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
