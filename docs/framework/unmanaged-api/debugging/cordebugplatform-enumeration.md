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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8cbf09ab4ad0192902a964d55a050685b024284
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574306"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="ec90e-102">CorDebugPlatform Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ec90e-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="ec90e-103">Tarafından kullanılan hedef platform değerleri sağlayan [Icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ec90e-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec90e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec90e-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="ec90e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ec90e-105">Members</span></span>  
  
|<span data-ttu-id="ec90e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ec90e-106">Member</span></span>|<span data-ttu-id="ec90e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec90e-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ec90e-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="ec90e-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="ec90e-109">Hedef, Intel x86 donanım üzerinde çalışan Windows platformudur.</span><span class="sxs-lookup"><span data-stu-id="ec90e-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="ec90e-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="ec90e-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="ec90e-111">Hedef, 64 bit Windows AMD64 veya Intel EM64T donanım üzerinde çalışan platformudur.</span><span class="sxs-lookup"><span data-stu-id="ec90e-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="ec90e-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="ec90e-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="ec90e-113">Hedef, Intel IA-64 donanım üzerinde çalışan 32 bit Windows platformudur.</span><span class="sxs-lookup"><span data-stu-id="ec90e-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="ec90e-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="ec90e-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="ec90e-115">Hedef, PowerPC donanımda çalışan Macintosh işletim sistemi platformudur.</span><span class="sxs-lookup"><span data-stu-id="ec90e-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="ec90e-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="ec90e-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="ec90e-117">Hedef, Intel x86 donanımda çalışan Macintosh işletim sistemi platformudur.</span><span class="sxs-lookup"><span data-stu-id="ec90e-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="ec90e-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="ec90e-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="ec90e-119">Windows ARM donanım üzerinde çalışan Macintosh işletim sistemini hedef platformudur.</span><span class="sxs-lookup"><span data-stu-id="ec90e-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="ec90e-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="ec90e-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="ec90e-121">Hedef platform AMD64 donanımda çalışan Macintosh işletim sistemi ' dir.</span><span class="sxs-lookup"><span data-stu-id="ec90e-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec90e-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec90e-122">Requirements</span></span>  
 <span data-ttu-id="ec90e-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec90e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec90e-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec90e-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec90e-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec90e-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec90e-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec90e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="ec90e-127">`CORDB_PLATFORM_WINDOWS_ARM` Ve `CORDB_PLATFORM_MAC_AMD64` üyeleri olan .NET Framework 4.5.2 ve sonraki sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec90e-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec90e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec90e-128">See also</span></span>
- [<span data-ttu-id="ec90e-129">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ec90e-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
