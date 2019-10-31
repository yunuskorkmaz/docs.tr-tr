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
ms.openlocfilehash: 826dfceb28512e4fd3157c432b7a4d94fba704fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097868"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="f0c80-102">CorDebugNGenPolicy Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f0c80-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="f0c80-103">Bir hata ayıklayıcının yerel görüntü önbelleğinden yerel (NGen) görüntüler yükleyip yüklemeyeceğini belirleyen bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0c80-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0c80-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0c80-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="f0c80-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f0c80-105">Members</span></span>  
  
|<span data-ttu-id="f0c80-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="f0c80-106">Member name</span></span>|<span data-ttu-id="f0c80-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0c80-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="f0c80-108">[!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] bir uygulamada yerel yerel görüntü önbelleğinden görüntülerin kullanımı devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="f0c80-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="f0c80-109">Bir masaüstü uygulamasında, bu ayarın etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f0c80-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0c80-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0c80-110">Remarks</span></span>  
 <span data-ttu-id="f0c80-111">`CorDebugNGENPolicy` numaralandırması, [ICorDebugProcess5:: EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0c80-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="f0c80-112">Yerel yerel görüntü önbelleğinden görüntülerin kullanımını devre dışı bırakmak, hata ayıklayıcının, en iyileştirilmiş yerel görüntüler yerine JıT derlenmiş görüntüleri hata ayıklanabilir yüklemelerini sağlayarak tutarlı bir hata ayıklama deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0c80-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0c80-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0c80-113">Requirements</span></span>  
 <span data-ttu-id="f0c80-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0c80-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0c80-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f0c80-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0c80-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f0c80-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0c80-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0c80-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c80-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0c80-118">See also</span></span>

- [<span data-ttu-id="f0c80-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f0c80-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
