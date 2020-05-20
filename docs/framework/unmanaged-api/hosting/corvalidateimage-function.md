---
title: _CorValidateImage İşlevi
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 8841fab0517353849ef99594bcbd03dda772c766
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616508"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="57a82-102">_CorValidateImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="57a82-102">_CorValidateImage Function</span></span>
<span data-ttu-id="57a82-103">Yönetilen modül görüntülerini doğrular ve yüklendikten sonra işletim sistemi yükleyicisini bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="57a82-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57a82-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="57a82-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57a82-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57a82-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="57a82-106">'ndaki Yönetilen kod olarak doğrulanacak görüntünün başlangıç konumuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57a82-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="57a82-107">Görüntü zaten belleğe yüklenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="57a82-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="57a82-108">'ndaki Görüntünün dosya adı.</span><span class="sxs-lookup"><span data-stu-id="57a82-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57a82-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="57a82-109">Return Value</span></span>  
 <span data-ttu-id="57a82-110">Bu işlev, `E_INVALIDARG` `E_OUTOFMEMORY` `E_UNEXPECTED` aşağıdaki değerleri ve,,, ve standart değerlerini döndürür `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="57a82-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="57a82-111">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="57a82-111">Return value</span></span>|<span data-ttu-id="57a82-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57a82-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="57a82-113">Görüntü geçersiz.</span><span class="sxs-lookup"><span data-stu-id="57a82-113">The image is invalid.</span></span> <span data-ttu-id="57a82-114">Bu değer HRESULT 0xC000007BL.</span><span class="sxs-lookup"><span data-stu-id="57a82-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="57a82-115">Görüntü geçerli.</span><span class="sxs-lookup"><span data-stu-id="57a82-115">The image is valid.</span></span> <span data-ttu-id="57a82-116">Bu değer HRESULT 0x00000000L ' i içerir.</span><span class="sxs-lookup"><span data-stu-id="57a82-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57a82-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57a82-117">Remarks</span></span>  
 <span data-ttu-id="57a82-118">Windows XP ve sonraki sürümlerinde, işletim sistemi yükleyicisi ortak nesne dosyası biçimi (COFF) üstbilgisindeki COM tanımlayıcı dizin bitini inceleyerek yönetilen modülleri denetler.</span><span class="sxs-lookup"><span data-stu-id="57a82-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="57a82-119">Set bit, yönetilen bir modülü gösterir.</span><span class="sxs-lookup"><span data-stu-id="57a82-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="57a82-120">Yükleyici yönetilen bir modül algılarsa, MsCorEE. dll ve çağrılarını yükler ve `_CorValidateImage` aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="57a82-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="57a82-121">Görüntünün geçerli bir yönetilen modül olduğunu onaylar.</span><span class="sxs-lookup"><span data-stu-id="57a82-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="57a82-122">Görüntüdeki giriş noktasını, ortak dil çalışma zamanında (CLR) bir giriş noktasına değiştirir.</span><span class="sxs-lookup"><span data-stu-id="57a82-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="57a82-123">Windows 'un 64 bitlik sürümleri için, bellekte bulunan görüntüyü PE32 ' dan PE32 + biçimine dönüştürerek değiştirir.</span><span class="sxs-lookup"><span data-stu-id="57a82-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="57a82-124">Yönetilen modül görüntüleri yüklendiğinde yükleyice döndürür.</span><span class="sxs-lookup"><span data-stu-id="57a82-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="57a82-125">Yürütülebilir görüntüler için, işletim sistemi yükleyicisi, yürütülebilir dosyada belirtilen giriş noktası ne olursa olsun [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="57a82-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="57a82-126">DLL derleme görüntüleri için yükleyici [_CorDllMain](cordllmain-function.md) işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="57a82-126">For DLL assembly images, the loader calls the [_CorDllMain](cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="57a82-127">`_CorExeMain`ya da `_CorDllMain` aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="57a82-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="57a82-128">CLR 'yi başlatır.</span><span class="sxs-lookup"><span data-stu-id="57a82-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="57a82-129">Yönetilen giriş noktasını derlemenin CLR üst bilgisinden konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="57a82-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="57a82-130">Yürütmeye başlar.</span><span class="sxs-lookup"><span data-stu-id="57a82-130">Begins execution.</span></span>  
  
 <span data-ttu-id="57a82-131">Yükleyici, yönetilen modül görüntüleri kaldırıldığında [_CorImageUnloading](corimageunloading-function.md) işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="57a82-131">The loader calls the [_CorImageUnloading](corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="57a82-132">Ancak, bu işlev herhangi bir eylem gerçekleştirmez; yalnızca döndürür.</span><span class="sxs-lookup"><span data-stu-id="57a82-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57a82-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57a82-133">Requirements</span></span>  
 <span data-ttu-id="57a82-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57a82-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57a82-135">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="57a82-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57a82-136">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="57a82-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57a82-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57a82-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57a82-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57a82-138">See also</span></span>

- [<span data-ttu-id="57a82-139">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="57a82-139">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
