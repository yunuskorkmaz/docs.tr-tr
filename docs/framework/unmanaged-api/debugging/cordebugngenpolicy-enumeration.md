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
ms.openlocfilehash: 036d3f12b38c19259fefaba674d0f9025a58d688
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795761"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="682b2-102">CorDebugNGenPolicy Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="682b2-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="682b2-103">Bir hata ayıklayıcının yerel görüntü önbelleğinden yerel (NGen) görüntüler yükleyip yüklemeyeceğini belirleyen bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="682b2-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="682b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="682b2-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="682b2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="682b2-105">Members</span></span>  
  
|<span data-ttu-id="682b2-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="682b2-106">Member name</span></span>|<span data-ttu-id="682b2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="682b2-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="682b2-108">Bir Windows 8. x Mağazası uygulamasında yerel yerel görüntü önbelleğinden görüntülerin kullanımı devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="682b2-108">In a Windows 8.x Store app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="682b2-109">Bir masaüstü uygulamasında, bu ayarın etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="682b2-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="682b2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="682b2-110">Remarks</span></span>  
 <span data-ttu-id="682b2-111">`CorDebugNGENPolicy` Numaralandırma, [ICorDebugProcess5:: EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="682b2-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="682b2-112">Yerel yerel görüntü önbelleğinden görüntülerin kullanımını devre dışı bırakmak, hata ayıklayıcının, en iyileştirilmiş yerel görüntüler yerine JıT derlenmiş görüntüleri hata ayıklanabilir yüklemelerini sağlayarak tutarlı bir hata ayıklama deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="682b2-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="682b2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="682b2-113">Requirements</span></span>  
 <span data-ttu-id="682b2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="682b2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="682b2-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="682b2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="682b2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="682b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="682b2-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="682b2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="682b2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="682b2-118">See also</span></span>

- [<span data-ttu-id="682b2-119">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="682b2-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
