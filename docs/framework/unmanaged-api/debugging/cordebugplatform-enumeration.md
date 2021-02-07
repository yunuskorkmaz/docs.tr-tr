---
description: 'Bu konuda daha fazla bilgi edinin: CorDebugPlatform numaralandırması'
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
ms.openlocfilehash: d6a78ec00f99ff34158f784e039372c8937e6d16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661863"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="5fce8-103">CorDebugPlatform Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5fce8-103">CorDebugPlatform Enumeration</span></span>

<span data-ttu-id="5fce8-104">[ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından kullanılan hedef platform değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fce8-104">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fce8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5fce8-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="5fce8-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5fce8-106">Members</span></span>  
  
|<span data-ttu-id="5fce8-107">Üye</span><span class="sxs-lookup"><span data-stu-id="5fce8-107">Member</span></span>|<span data-ttu-id="5fce8-108">Description</span><span class="sxs-lookup"><span data-stu-id="5fce8-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5fce8-109">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="5fce8-109">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="5fce8-110">Hedef platform, Intel x86 donanımında çalışan bir Windows.</span><span class="sxs-lookup"><span data-stu-id="5fce8-110">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="5fce8-111">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="5fce8-111">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="5fce8-112">Hedef platform, AMD64 veya Intel EM64T donanımında çalışan 64 bitlik bir Windows.</span><span class="sxs-lookup"><span data-stu-id="5fce8-112">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="5fce8-113">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="5fce8-113">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="5fce8-114">Hedef platform Intel IA-64 donanımında çalışan 32 bit Windows.</span><span class="sxs-lookup"><span data-stu-id="5fce8-114">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="5fce8-115">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="5fce8-115">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="5fce8-116">Hedef platform, PowerPC donanımında çalışan Macintosh işletim sistemidir.</span><span class="sxs-lookup"><span data-stu-id="5fce8-116">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="5fce8-117">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="5fce8-117">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="5fce8-118">Hedef platform, Intel x86 donanımında çalışan Macintosh işletim sistemidir.</span><span class="sxs-lookup"><span data-stu-id="5fce8-118">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="5fce8-119">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="5fce8-119">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="5fce8-120">Hedef platform, Windows ARM donanımında çalışan Macintosh işletim sistemidir.</span><span class="sxs-lookup"><span data-stu-id="5fce8-120">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="5fce8-121">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="5fce8-121">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="5fce8-122">Hedef platform, AMD64 donanımında çalışan Macintosh işletim sistemidir.</span><span class="sxs-lookup"><span data-stu-id="5fce8-122">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5fce8-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5fce8-123">Requirements</span></span>  

 <span data-ttu-id="5fce8-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fce8-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fce8-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5fce8-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fce8-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5fce8-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fce8-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fce8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="5fce8-128">`CORDB_PLATFORM_WINDOWS_ARM`Ve `CORDB_PLATFORM_MAC_AMD64` üyeleri .NET Framework 4.5.2 ve sonraki sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fce8-128">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fce8-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fce8-129">See also</span></span>

- [<span data-ttu-id="5fce8-130">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="5fce8-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
