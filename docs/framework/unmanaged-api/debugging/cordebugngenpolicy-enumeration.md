---
title: CorDebugNGenPolicy Sabit Listesi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca922d8b582c0608073d4fd0ba986167ae470e34
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109674"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="9778a-102">CorDebugNGenPolicy Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9778a-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="9778a-103">Bir hata ayıklayıcı yerel görüntü önbelleğinden kaldırırız (NGen) yerel görüntüleri yükleyip yüklemediğini belirleyen bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="9778a-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9778a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9778a-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="9778a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9778a-105">Members</span></span>  
  
|<span data-ttu-id="9778a-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="9778a-106">Member name</span></span>|<span data-ttu-id="9778a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9778a-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="9778a-108">İçinde bir [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] uygulama, görüntüleri yerel görüntü önbelleğinden kullanımını devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9778a-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="9778a-109">İçinde bir masaüstü uygulaması, bu ayar etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="9778a-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9778a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9778a-110">Remarks</span></span>  
 <span data-ttu-id="9778a-111">`CorDebugNGENPolicy` Numaralandırması tarafından kullanılan [Icordebugprocess5::enablengenpolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9778a-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="9778a-112">Görüntüleri yerel görüntü önbelleğinden kullanımını devre dışı bırakma, hata ayıklayıcı hata ayıklanabilir JIT olarak derlenmiş görüntüleri yerine en iyi duruma getirilmiş yerel görüntüleri yükler sağlayarak için tutarlı bir hata ayıklama deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9778a-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9778a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9778a-113">Requirements</span></span>  
 <span data-ttu-id="9778a-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9778a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9778a-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9778a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9778a-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9778a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9778a-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9778a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9778a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9778a-118">See also</span></span>

- [<span data-ttu-id="9778a-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="9778a-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
