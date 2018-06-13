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
ms.openlocfilehash: cc5a06e6b3cc1e9338d860cdb110bf7d516080be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404030"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="13f5c-102">CorDebugNGenPolicy Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="13f5c-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="13f5c-103">Bir hata ayıklayıcısı yerel görüntü önbellekten yerel (NGen) görüntüler yükler olup olmadığını belirleyen bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="13f5c-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13f5c-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="13f5c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="13f5c-105">Members</span></span>  
  
|<span data-ttu-id="13f5c-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="13f5c-106">Member name</span></span>|<span data-ttu-id="13f5c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13f5c-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="13f5c-108">İçinde bir [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] uygulama, yerel yerel görüntü önbelleği görüntülerden kullanımını devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="13f5c-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="13f5c-109">Bir masaüstü uygulamasının bu ayarın etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="13f5c-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13f5c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13f5c-110">Remarks</span></span>  
 <span data-ttu-id="13f5c-111">`CorDebugNGENPolicy` Numaralandırması tarafından kullanılan [Icordebugprocess5::enablengenpolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="13f5c-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="13f5c-112">Yerel yerel görüntü önbelleği görüntülerden kullanımını devre dışı bırakma, hata ayıklayıcı en iyi duruma getirilmiş yerel görüntüler yerine debuggable JIT derlenmiş görüntüleri yükler sağlayarak için hata ayıklama tutarlı bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="13f5c-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13f5c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13f5c-113">Requirements</span></span>  
 <span data-ttu-id="13f5c-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13f5c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13f5c-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13f5c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13f5c-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13f5c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13f5c-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13f5c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f5c-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13f5c-118">See Also</span></span>  
 [<span data-ttu-id="13f5c-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="13f5c-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
