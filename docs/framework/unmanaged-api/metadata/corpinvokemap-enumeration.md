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
ms.openlocfilehash: 17b7af7016cf88fd3ae263dd952502d515b0c833
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441563"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="b5446-102">CorPinvokeMap Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b5446-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="b5446-103">PInvoke çağrısı seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5446-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5446-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5446-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b5446-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b5446-105">Members</span></span>  
  
|<span data-ttu-id="b5446-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b5446-106">Member</span></span>|<span data-ttu-id="b5446-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5446-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="b5446-108">Her üye adını belirtilen şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5446-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="b5446-109">Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="b5446-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="b5446-110">Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="b5446-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="b5446-111">Dizeleri birden çok baytlık karakter dizesi olarak sıralama.</span><span class="sxs-lookup"><span data-stu-id="b5446-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="b5446-112">Dizeleri Unicode 2 baytlık karakterler olarak sıralama.</span><span class="sxs-lookup"><span data-stu-id="b5446-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="b5446-113">Dizeleri hedef işletim sistemi için uygun şekilde otomatik olarak sıralama.</span><span class="sxs-lookup"><span data-stu-id="b5446-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="b5446-114">Varsayılan değer Windows NT, Windows 2000, Windows XP ve Windows Server 2003 ailesi için Unicode 'dur; Varsayılan değer Windows 98 ve Windows Me 'de ANSI 'dir.</span><span class="sxs-lookup"><span data-stu-id="b5446-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="b5446-115">Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="b5446-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="b5446-116">ANSI karakter kümesinde tam eşleşme olmayan Unicode karakterlerinin en iyi şekilde eşleşmesini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="b5446-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="b5446-117">Unicode karakterlerin en iyi şekilde eşleşmesini gerçekleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="b5446-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="b5446-118">Bu durumda, tüm eşlenebilir karakterler '? ' ile değiştirilirler.</span><span class="sxs-lookup"><span data-stu-id="b5446-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="b5446-119">Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="b5446-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="b5446-120">Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="b5446-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="b5446-121">Birlikte çalışma sıralayıcısı, eşlenebilir bir karakterle karşılaştığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5446-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="b5446-122">Birlikte çalışma sıralayıcısı, eşlenebilir bir karakterle karşılaştığında özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="b5446-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="b5446-123">Ayrılmış</span><span class="sxs-lookup"><span data-stu-id="b5446-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="b5446-124">Aranan yöntemden dönmeden önce çağrılan tarafından Win32 `SetLastError` işlevini çağırmaya izin verin.</span><span class="sxs-lookup"><span data-stu-id="b5446-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="b5446-125">Ayrılmış</span><span class="sxs-lookup"><span data-stu-id="b5446-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="b5446-126">Varsayılan platform çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5446-126">Use the default platform calling convention.</span></span> <span data-ttu-id="b5446-127">Örneğin, Windows 'da varsayılan değer `StdCall` ve Windows CE .NET ' de `Cdecl`.</span><span class="sxs-lookup"><span data-stu-id="b5446-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="b5446-128">`Cdecl` çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5446-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="b5446-129">Bu durumda, çağıran yığını temizler.</span><span class="sxs-lookup"><span data-stu-id="b5446-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="b5446-130">Bu, işlevleri `varargs` (bir değişken parametre sayısı kabul eden işlevler) ile çağırma imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="b5446-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="b5446-131">`StdCall` çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5446-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="b5446-132">Bu durumda, çağrılan yığını temizler.</span><span class="sxs-lookup"><span data-stu-id="b5446-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="b5446-133">Bu, platform Invoke ile yönetilmeyen işlevleri çağırmak için varsayılan kuraldır.</span><span class="sxs-lookup"><span data-stu-id="b5446-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="b5446-134">`ThisCall` çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5446-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="b5446-135">Bu durumda, ilk parametre `this` işaretçisidir ve Register ECX konumunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="b5446-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="b5446-136">Diğer parametreler yığına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b5446-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="b5446-137">`ThisCall` çağırma kuralı, yönetilmeyen bir DLL 'den aktarılmış sınıflarda yöntemleri çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b5446-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="b5446-138">Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="b5446-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="b5446-139">Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="b5446-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5446-140">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5446-140">Requirements</span></span>  
 <span data-ttu-id="b5446-141">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5446-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5446-142">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b5446-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b5446-143">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5446-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5446-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5446-144">See also</span></span>

- [<span data-ttu-id="b5446-145">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b5446-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
