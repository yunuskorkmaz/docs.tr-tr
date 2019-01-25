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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23a4c1aa25f269121dc602bbeb6b864b589318be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745991"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="d620a-102">CorPinvokeMap Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d620a-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="d620a-103">PInvoke arama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d620a-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d620a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d620a-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="d620a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d620a-105">Members</span></span>  
  
|<span data-ttu-id="d620a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d620a-106">Member</span></span>|<span data-ttu-id="d620a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d620a-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="d620a-108">Belirtilen üye adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="d620a-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="d620a-109">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d620a-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="d620a-110">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d620a-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="d620a-111">Birden çok baytlı karakter dizeleri olarak dizelerini sıralama.</span><span class="sxs-lookup"><span data-stu-id="d620a-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="d620a-112">2 baytlık karakterler Unicode dizelerini sıralama.</span><span class="sxs-lookup"><span data-stu-id="d620a-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="d620a-113">Otomatik olarak hedef işletim sistemi için uygun şekilde dizeleri sıralaması.</span><span class="sxs-lookup"><span data-stu-id="d620a-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="d620a-114">Varsayılan Windows NT, Windows 2000, Windows XP ve Windows Server 2003 ailesinin Unicode bulunur. Windows 98 ve Windows Me ANSI varsayılandır</span><span class="sxs-lookup"><span data-stu-id="d620a-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="d620a-115">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d620a-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="d620a-116">En iyi uyan eşlemeyi ANSI karakter kümesi içinde bir tam eşleşme eksik Unicode karakter gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="d620a-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="d620a-117">Unicode karakter en iyi uyan eşlemeyi gerçekleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="d620a-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="d620a-118">Bu durumda, tüm eşlenemez karakterleri ile değiştirilecek bir '?'.</span><span class="sxs-lookup"><span data-stu-id="d620a-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="d620a-119">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d620a-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="d620a-120">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d620a-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="d620a-121">Birlikte çalışma sıralayıcısı eşlenemez bir karakterle karşılaştığında bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="d620a-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="d620a-122">Birlikte çalışma sıralayıcısı eşlenemez bir karakterle karşılaştığında bir özel durum oluşturması beklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="d620a-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="d620a-123">Ayrılmış</span><span class="sxs-lookup"><span data-stu-id="d620a-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="d620a-124">Win32 çağırmak Aranan izin `SetLastError` öznitelikli yöntemini döndürmeden önce işlevi.</span><span class="sxs-lookup"><span data-stu-id="d620a-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="d620a-125">Ayrılmış</span><span class="sxs-lookup"><span data-stu-id="d620a-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="d620a-126">Varsayılan platform çağırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d620a-126">Use the default platform calling convention.</span></span> <span data-ttu-id="d620a-127">Örneğin, Windows üzerinde varsayılandır `StdCall` ve Windows CE olduğu .NET `Cdecl`.</span><span class="sxs-lookup"><span data-stu-id="d620a-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="d620a-128">Kullanım `Cdecl` çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="d620a-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="d620a-129">Bu durumda, çağıranın yığını temizler.</span><span class="sxs-lookup"><span data-stu-id="d620a-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="d620a-130">Bu, arama işlevlerinde sağlar `varargs` (diğer bir deyişle, değişik sayıda parametreyi kabul eden işlevler).</span><span class="sxs-lookup"><span data-stu-id="d620a-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="d620a-131">Kullanım `StdCall` çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="d620a-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="d620a-132">Bu durumda, çağrılan yığını temizler.</span><span class="sxs-lookup"><span data-stu-id="d620a-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="d620a-133">Bu, yönetilmeyen işlevleri çağırma platformuyla çağırmak için varsayılan kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="d620a-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="d620a-134">Kullanım `ThisCall` çağırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="d620a-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="d620a-135">Bu durumda ilk parametresinin olup `this` işaretçisi ve kayıtta ECX depolanır.</span><span class="sxs-lookup"><span data-stu-id="d620a-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="d620a-136">Diğer parametreler, yığın üzerine itilir.</span><span class="sxs-lookup"><span data-stu-id="d620a-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="d620a-137">`ThisCall` Çağırma yöntemleri yönetilmeyen DLL dosyasından dışarı aktarılan sınıflar çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d620a-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="d620a-138">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d620a-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="d620a-139">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d620a-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d620a-140">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d620a-140">Requirements</span></span>  
 <span data-ttu-id="d620a-141">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d620a-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d620a-142">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d620a-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d620a-143">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d620a-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d620a-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d620a-144">See also</span></span>
- [<span data-ttu-id="d620a-145">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d620a-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
