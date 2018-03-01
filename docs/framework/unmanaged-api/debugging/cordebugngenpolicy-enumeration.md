---
title: CorDebugNGenPolicy Sabit Listesi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 89767da7178319ed1add3dda0620062893487bfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="c636b-102">CorDebugNGenPolicy Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c636b-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="c636b-103">Bir hata ayıklayıcısı yerel görüntü önbellekten yerel (NGen) görüntüler yükler olup olmadığını belirleyen bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="c636b-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c636b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c636b-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="c636b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c636b-105">Members</span></span>  
  
|<span data-ttu-id="c636b-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="c636b-106">Member name</span></span>|<span data-ttu-id="c636b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c636b-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="c636b-108">İçinde bir [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] uygulama, yerel yerel görüntü önbelleği görüntülerden kullanımını devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c636b-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="c636b-109">Bir masaüstü uygulamasının bu ayarın etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c636b-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c636b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c636b-110">Remarks</span></span>  
 <span data-ttu-id="c636b-111">`CorDebugNGENPolicy` Numaralandırması tarafından kullanılan [Icordebugprocess5::enablengenpolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c636b-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="c636b-112">Yerel yerel görüntü önbelleği görüntülerden kullanımını devre dışı bırakma, hata ayıklayıcı en iyi duruma getirilmiş yerel görüntüler yerine debuggable JIT derlenmiş görüntüleri yükler sağlayarak için hata ayıklama tutarlı bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="c636b-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c636b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c636b-113">Requirements</span></span>  
 <span data-ttu-id="c636b-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c636b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c636b-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c636b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c636b-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c636b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c636b-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c636b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c636b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c636b-118">See Also</span></span>  
 [<span data-ttu-id="c636b-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c636b-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
