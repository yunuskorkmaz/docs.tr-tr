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
ms.openlocfilehash: da3ee54b1c3361149c11a9cfad8bdb07a5007ecf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706157"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="d7198-102">CorPinvokeMap Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d7198-102">CorPinvokeMap Enumeration</span></span>

<span data-ttu-id="d7198-103">PInvoke çağrısı seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7198-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7198-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d7198-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d7198-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d7198-105">Members</span></span>  
  
|<span data-ttu-id="d7198-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d7198-106">Member</span></span>|<span data-ttu-id="d7198-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7198-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="d7198-108">Her üye adını belirtilen şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7198-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="d7198-109">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d7198-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="d7198-110">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d7198-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="d7198-111">Dizeleri birden çok baytlık karakter dizesi olarak sıralama.</span><span class="sxs-lookup"><span data-stu-id="d7198-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="d7198-112">Dizeleri Unicode 2 baytlık karakterler olarak sıralama.</span><span class="sxs-lookup"><span data-stu-id="d7198-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="d7198-113">Dizeleri hedef işletim sistemi için uygun şekilde otomatik olarak sıralama.</span><span class="sxs-lookup"><span data-stu-id="d7198-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="d7198-114">Varsayılan değer Windows NT, Windows 2000, Windows XP ve Windows Server 2003 ailesi için Unicode 'dur; Varsayılan değer Windows 98 ve Windows Me 'de ANSI 'dir.</span><span class="sxs-lookup"><span data-stu-id="d7198-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="d7198-115">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d7198-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="d7198-116">ANSI karakter kümesinde tam eşleşme olmayan Unicode karakterlerinin en iyi şekilde eşleşmesini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="d7198-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="d7198-117">Unicode karakterlerin en iyi şekilde eşleşmesini gerçekleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="d7198-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="d7198-118">Bu durumda, tüm eşlenebilir karakterler '? ' ile değiştirilirler.</span><span class="sxs-lookup"><span data-stu-id="d7198-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="d7198-119">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d7198-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="d7198-120">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d7198-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="d7198-121">Birlikte çalışma sıralayıcısı, eşlenebilir bir karakterle karşılaştığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d7198-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="d7198-122">Birlikte çalışma sıralayıcısı, eşlenebilir bir karakterle karşılaştığında özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="d7198-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="d7198-123">Ayrılmıştır</span><span class="sxs-lookup"><span data-stu-id="d7198-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="d7198-124">Aranan `SetLastError` yöntemden dönmeden önce çağrılan tarafından Win32 işlevini çağırmaya izin verin.</span><span class="sxs-lookup"><span data-stu-id="d7198-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="d7198-125">Ayrılmıştır</span><span class="sxs-lookup"><span data-stu-id="d7198-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="d7198-126">Varsayılan platform çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7198-126">Use the default platform calling convention.</span></span> <span data-ttu-id="d7198-127">Örneğin, Windows 'ta varsayılan olarak `StdCall` ve Windows CE .net ' dir `Cdecl` .</span><span class="sxs-lookup"><span data-stu-id="d7198-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="d7198-128">`Cdecl`Çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7198-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="d7198-129">Bu durumda, çağıran yığını temizler.</span><span class="sxs-lookup"><span data-stu-id="d7198-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="d7198-130">Bu, işlevleri çağırma `varargs` (diğer bir deyişle, değişken sayıda parametre kabul eden işlevler) sunar.</span><span class="sxs-lookup"><span data-stu-id="d7198-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="d7198-131">`StdCall`Çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7198-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="d7198-132">Bu durumda, çağrılan yığını temizler.</span><span class="sxs-lookup"><span data-stu-id="d7198-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="d7198-133">Bu, platform Invoke ile yönetilmeyen işlevleri çağırmak için varsayılan kuraldır.</span><span class="sxs-lookup"><span data-stu-id="d7198-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="d7198-134">`ThisCall`Çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7198-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="d7198-135">Bu durumda, ilk parametre `this` işaretçisidir ve Register ECX konumunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="d7198-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="d7198-136">Diğer parametreler yığına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="d7198-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="d7198-137">`ThisCall`Çağırma kuralı, yönetilmeyen BIR DLL 'den aktarılmış sınıflarda yöntemleri çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7198-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="d7198-138">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d7198-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="d7198-139">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d7198-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7198-140">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7198-140">Requirements</span></span>  

 <span data-ttu-id="d7198-141">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7198-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7198-142">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d7198-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d7198-143">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7198-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7198-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7198-144">See also</span></span>

- [<span data-ttu-id="d7198-145">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="d7198-145">Metadata Enumerations</span></span>](metadata-enumerations.md)
