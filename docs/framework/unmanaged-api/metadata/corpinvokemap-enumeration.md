---
title: CorPinvokeMap Numaralandırması
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176155"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="7289a-102">CorPinvokeMap Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7289a-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="7289a-103">Bir PInvoke araması için seçenekleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7289a-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7289a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7289a-104">Syntax</span></span>  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="7289a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7289a-105">Members</span></span>  
  
|<span data-ttu-id="7289a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7289a-106">Member</span></span>|<span data-ttu-id="7289a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7289a-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="7289a-108">Belirtilen her üye adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7289a-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="7289a-109">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7289a-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="7289a-110">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7289a-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="7289a-111">Mareşal dizeleri çoklu bayt karakter dizeleri olarak.</span><span class="sxs-lookup"><span data-stu-id="7289a-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="7289a-112">Unicode 2-bayt karakterleri olarak Mareşal dizeleri.</span><span class="sxs-lookup"><span data-stu-id="7289a-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="7289a-113">Dizeleri hedef işletim sistemi için uygun şekilde otomatik olarak mareşal.</span><span class="sxs-lookup"><span data-stu-id="7289a-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="7289a-114">Varsayılan olarak Windows NT, Windows 2000, Windows XP ve Windows Server 2003 ailesindeki Unicode; varsayılan Windows 98 ve Windows Me'deki ANSI'dir.</span><span class="sxs-lookup"><span data-stu-id="7289a-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="7289a-115">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7289a-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="7289a-116">ANSI karakter kümesinde tam eşleşme olmayan Unicode karakterlerinin en uygun eşlenemesini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="7289a-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="7289a-117">Unicode karakterlerinin en uygun eşlemesi gerçekleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="7289a-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="7289a-118">Bu durumda, eşlenemeyecek tüm karakterler '?' ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="7289a-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="7289a-119">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7289a-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="7289a-120">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7289a-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="7289a-121">Interop mareşal eşlenebilir bir karakter karşılaştığında bir özel durum atın.</span><span class="sxs-lookup"><span data-stu-id="7289a-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="7289a-122">Interop mareşal eşlenebilir bir karakter karşılaştığında bir özel durum atmayın.</span><span class="sxs-lookup"><span data-stu-id="7289a-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="7289a-123">Ayrıldı</span><span class="sxs-lookup"><span data-stu-id="7289a-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="7289a-124">Atfedilen yöntemden dönmeden önce `SetLastError` callee'nin Win32 işlevini aramasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="7289a-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="7289a-125">Ayrıldı</span><span class="sxs-lookup"><span data-stu-id="7289a-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="7289a-126">Varsayılan çağrı kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7289a-126">Use the default platform calling convention.</span></span> <span data-ttu-id="7289a-127">Örneğin, Windows'da varsayılan `StdCall` ve Windows CE .NET'te . `Cdecl`</span><span class="sxs-lookup"><span data-stu-id="7289a-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="7289a-128">Arama `Cdecl` kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7289a-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="7289a-129">Bu durumda, arayan yığını temizler.</span><span class="sxs-lookup"><span data-stu-id="7289a-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="7289a-130">Bu, (değişken `varargs` sayıda parametre kabul eden işlevler) ile arama işlevlerini etkinleştirmektedir.</span><span class="sxs-lookup"><span data-stu-id="7289a-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="7289a-131">Arama `StdCall` kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7289a-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="7289a-132">Bu durumda, callee yığını temizler.</span><span class="sxs-lookup"><span data-stu-id="7289a-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="7289a-133">Bu, yönetilmeyen işlevleri platform çağrısıyla çağırmak için varsayılan kuraldır.</span><span class="sxs-lookup"><span data-stu-id="7289a-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="7289a-134">Arama `ThisCall` kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7289a-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="7289a-135">Bu durumda, ilk parametre `this` işaretçidir ve kayıt ECX'te depolanır.</span><span class="sxs-lookup"><span data-stu-id="7289a-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="7289a-136">Diğer parametreler yığına itilir.</span><span class="sxs-lookup"><span data-stu-id="7289a-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="7289a-137">Çağrı `ThisCall` kuralı, yönetilmeyen bir DLL'den dışa aktarılan sınıflardaki yöntemleri çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7289a-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="7289a-138">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7289a-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="7289a-139">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7289a-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7289a-140">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7289a-140">Requirements</span></span>  
 <span data-ttu-id="7289a-141">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7289a-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7289a-142">**Üstbilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="7289a-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7289a-143">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7289a-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7289a-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7289a-144">See also</span></span>

- [<span data-ttu-id="7289a-145">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="7289a-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
