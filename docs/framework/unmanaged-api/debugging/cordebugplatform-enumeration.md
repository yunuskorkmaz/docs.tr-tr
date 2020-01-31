---
title: CorDebugPlatform Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
ms.openlocfilehash: 2ed32449c4a133e6e72ec44f9cb57f49de22164a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778237"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="bf6a9-102">CorDebugPlatform Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bf6a9-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="bf6a9-103">[ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından kullanılan hedef platform değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf6a9-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf6a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf6a9-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a><span data-ttu-id="bf6a9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf6a9-105">Members</span></span>  
  
|<span data-ttu-id="bf6a9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bf6a9-106">Member</span></span>|<span data-ttu-id="bf6a9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf6a9-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bf6a9-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="bf6a9-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="bf6a9-109">Hedef platform, Intel x86 donanımında çalışan bir Windows.</span><span class="sxs-lookup"><span data-stu-id="bf6a9-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="bf6a9-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="bf6a9-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="bf6a9-111">Hedef platform, AMD64 veya Intel EM64T donanımında çalışan 64 bitlik bir Windows.</span><span class="sxs-lookup"><span data-stu-id="bf6a9-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="bf6a9-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="bf6a9-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="bf6a9-113">Hedef platform Intel IA-64 donanımında çalışan 32 bit Windows.</span><span class="sxs-lookup"><span data-stu-id="bf6a9-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="bf6a9-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="bf6a9-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="bf6a9-115">Hedef platform, PowerPC donanımında çalışan Macintosh işletim sistemidir.</span><span class="sxs-lookup"><span data-stu-id="bf6a9-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="bf6a9-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="bf6a9-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="bf6a9-117">Hedef platform, Intel x86 donanımında çalışan Macintosh işletim sistemidir.</span><span class="sxs-lookup"><span data-stu-id="bf6a9-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="bf6a9-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="bf6a9-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="bf6a9-119">Hedef platform, Windows ARM donanımında çalışan Macintosh işletim sistemidir.</span><span class="sxs-lookup"><span data-stu-id="bf6a9-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="bf6a9-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="bf6a9-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="bf6a9-121">Hedef platform, AMD64 donanımında çalışan Macintosh işletim sistemidir.</span><span class="sxs-lookup"><span data-stu-id="bf6a9-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bf6a9-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf6a9-122">Requirements</span></span>  
 <span data-ttu-id="bf6a9-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf6a9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf6a9-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bf6a9-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf6a9-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bf6a9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf6a9-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf6a9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="bf6a9-127">`CORDB_PLATFORM_WINDOWS_ARM` ve `CORDB_PLATFORM_MAC_AMD64` üyeleri .NET Framework 4.5.2 ve sonraki sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf6a9-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf6a9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf6a9-128">See also</span></span>

- [<span data-ttu-id="bf6a9-129">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="bf6a9-129">Debugging Enumerations</span></span>](debugging-enumerations.md)
