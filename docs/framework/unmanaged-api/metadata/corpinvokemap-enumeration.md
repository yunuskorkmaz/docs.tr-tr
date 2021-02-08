---
description: 'Daha fazla bilgi edinin: Corpınvokemap sabit listesi'
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
ms.openlocfilehash: 8285632725096b4e6afc85fe54a89f12fc899dd1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784268"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="e8b0d-103">CorPinvokeMap Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e8b0d-103">CorPinvokeMap Enumeration</span></span>

<span data-ttu-id="e8b0d-104">PInvoke çağrısı seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-104">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8b0d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e8b0d-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="e8b0d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e8b0d-106">Members</span></span>  
  
|<span data-ttu-id="e8b0d-107">Üye</span><span class="sxs-lookup"><span data-stu-id="e8b0d-107">Member</span></span>|<span data-ttu-id="e8b0d-108">Description</span><span class="sxs-lookup"><span data-stu-id="e8b0d-108">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="e8b0d-109">Her üye adını belirtilen şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-109">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="e8b0d-110">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-110">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="e8b0d-111">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-111">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="e8b0d-112">Dizeleri birden çok baytlık karakter dizesi olarak sıralama.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-112">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="e8b0d-113">Dizeleri Unicode 2 baytlık karakterler olarak sıralama.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-113">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="e8b0d-114">Dizeleri hedef işletim sistemi için uygun şekilde otomatik olarak sıralama.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-114">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="e8b0d-115">Varsayılan değer Windows NT, Windows 2000, Windows XP ve Windows Server 2003 ailesi için Unicode 'dur; Varsayılan değer Windows 98 ve Windows Me 'de ANSI 'dir.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-115">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="e8b0d-116">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-116">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="e8b0d-117">ANSI karakter kümesinde tam eşleşme olmayan Unicode karakterlerinin en iyi şekilde eşleşmesini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-117">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="e8b0d-118">Unicode karakterlerin en iyi şekilde eşleşmesini gerçekleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-118">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="e8b0d-119">Bu durumda, tüm eşlenebilir karakterler '? ' ile değiştirilirler.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-119">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="e8b0d-120">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="e8b0d-121">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-121">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="e8b0d-122">Birlikte çalışma sıralayıcısı, eşlenebilir bir karakterle karşılaştığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-122">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="e8b0d-123">Birlikte çalışma sıralayıcısı, eşlenebilir bir karakterle karşılaştığında özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-123">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="e8b0d-124">Ayrılmıştır</span><span class="sxs-lookup"><span data-stu-id="e8b0d-124">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="e8b0d-125">Aranan `SetLastError` yöntemden dönmeden önce çağrılan tarafından Win32 işlevini çağırmaya izin verin.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-125">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="e8b0d-126">Ayrılmıştır</span><span class="sxs-lookup"><span data-stu-id="e8b0d-126">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="e8b0d-127">Varsayılan platform çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-127">Use the default platform calling convention.</span></span> <span data-ttu-id="e8b0d-128">Örneğin, Windows 'ta varsayılan olarak `StdCall` ve Windows CE .net ' dir `Cdecl` .</span><span class="sxs-lookup"><span data-stu-id="e8b0d-128">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="e8b0d-129">`Cdecl`Çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-129">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="e8b0d-130">Bu durumda, çağıran yığını temizler.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-130">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="e8b0d-131">Bu, işlevleri çağırma `varargs` (diğer bir deyişle, değişken sayıda parametre kabul eden işlevler) sunar.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-131">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="e8b0d-132">`StdCall`Çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-132">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="e8b0d-133">Bu durumda, çağrılan yığını temizler.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-133">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="e8b0d-134">Bu, platform Invoke ile yönetilmeyen işlevleri çağırmak için varsayılan kuraldır.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-134">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="e8b0d-135">`ThisCall`Çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-135">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="e8b0d-136">Bu durumda, ilk parametre `this` işaretçisidir ve Register ECX konumunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-136">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="e8b0d-137">Diğer parametreler yığına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-137">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="e8b0d-138">`ThisCall`Çağırma kuralı, yönetilmeyen BIR DLL 'den aktarılmış sınıflarda yöntemleri çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-138">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="e8b0d-139">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-139">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="e8b0d-140">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-140">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8b0d-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8b0d-141">Requirements</span></span>  

 <span data-ttu-id="e8b0d-142">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8b0d-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8b0d-143">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e8b0d-143">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e8b0d-144">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8b0d-144">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b0d-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8b0d-145">See also</span></span>

- [<span data-ttu-id="e8b0d-146">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="e8b0d-146">Metadata Enumerations</span></span>](metadata-enumerations.md)
