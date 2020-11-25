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
ms.openlocfilehash: 5435f78b28975a5426fcb2fce94904efc1051c5b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696407"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="50c5a-102">CorDebugPlatform Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="50c5a-102">CorDebugPlatform Enumeration</span></span>

<span data-ttu-id="50c5a-103">[ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından kullanılan hedef platform değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="50c5a-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50c5a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="50c5a-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="50c5a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="50c5a-105">Members</span></span>  
  
|<span data-ttu-id="50c5a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="50c5a-106">Member</span></span>|<span data-ttu-id="50c5a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50c5a-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="50c5a-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="50c5a-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="50c5a-109">Hedef platform, Intel x86 donanımında çalışan bir Windows.</span><span class="sxs-lookup"><span data-stu-id="50c5a-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="50c5a-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="50c5a-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="50c5a-111">Hedef platform, AMD64 veya Intel EM64T donanımında çalışan 64 bitlik bir Windows.</span><span class="sxs-lookup"><span data-stu-id="50c5a-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="50c5a-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="50c5a-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="50c5a-113">Hedef platform Intel IA-64 donanımında çalışan 32 bit Windows.</span><span class="sxs-lookup"><span data-stu-id="50c5a-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="50c5a-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="50c5a-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="50c5a-115">Hedef platform, PowerPC donanımında çalışan Macintosh işletim sistemidir.</span><span class="sxs-lookup"><span data-stu-id="50c5a-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="50c5a-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="50c5a-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="50c5a-117">Hedef platform, Intel x86 donanımında çalışan Macintosh işletim sistemidir.</span><span class="sxs-lookup"><span data-stu-id="50c5a-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="50c5a-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="50c5a-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="50c5a-119">Hedef platform, Windows ARM donanımında çalışan Macintosh işletim sistemidir.</span><span class="sxs-lookup"><span data-stu-id="50c5a-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="50c5a-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="50c5a-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="50c5a-121">Hedef platform, AMD64 donanımında çalışan Macintosh işletim sistemidir.</span><span class="sxs-lookup"><span data-stu-id="50c5a-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50c5a-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50c5a-122">Requirements</span></span>  

 <span data-ttu-id="50c5a-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50c5a-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50c5a-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="50c5a-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50c5a-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="50c5a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50c5a-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50c5a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="50c5a-127">`CORDB_PLATFORM_WINDOWS_ARM`Ve `CORDB_PLATFORM_MAC_AMD64` üyeleri .NET Framework 4.5.2 ve sonraki sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50c5a-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c5a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50c5a-128">See also</span></span>

- [<span data-ttu-id="50c5a-129">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="50c5a-129">Debugging Enumerations</span></span>](debugging-enumerations.md)
