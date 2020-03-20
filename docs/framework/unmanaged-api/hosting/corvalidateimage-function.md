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
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178210"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="6056c-102">_CorValidateImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="6056c-102">_CorValidateImage Function</span></span>
<span data-ttu-id="6056c-103">Yönetilen modül görüntülerini doğrular ve yüklendikten sonra işletim sistemi yükleyicisini onaylar.</span><span class="sxs-lookup"><span data-stu-id="6056c-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6056c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6056c-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6056c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6056c-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="6056c-106">[içinde] Yönetilen kod olarak doğrulamak için görüntünün başlangıç konumuna bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6056c-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="6056c-107">Görüntü zaten belleğe yüklenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6056c-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="6056c-108">[içinde] Resmin dosya adı.</span><span class="sxs-lookup"><span data-stu-id="6056c-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6056c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6056c-109">Return Value</span></span>  
 <span data-ttu-id="6056c-110">Bu işlev standart `E_INVALIDARG`değerleri `E_OUTOFMEMORY` `E_UNEXPECTED`, `E_FAIL`, , ve , yanı sıra aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6056c-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="6056c-111">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="6056c-111">Return value</span></span>|<span data-ttu-id="6056c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6056c-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="6056c-113">Görüntü geçersiz.</span><span class="sxs-lookup"><span data-stu-id="6056c-113">The image is invalid.</span></span> <span data-ttu-id="6056c-114">Bu değer HRESULT 0xC000007BL vardır.</span><span class="sxs-lookup"><span data-stu-id="6056c-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="6056c-115">Görüntü geçerli.</span><span class="sxs-lookup"><span data-stu-id="6056c-115">The image is valid.</span></span> <span data-ttu-id="6056c-116">Bu değer HRESULT 0x00000000L vardır.</span><span class="sxs-lookup"><span data-stu-id="6056c-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6056c-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6056c-117">Remarks</span></span>  
 <span data-ttu-id="6056c-118">Windows XP ve sonraki sürümlerde, işletim sistemi yükleyiciortak nesne dosya biçimi (COFF) üstbilgisinde COM Tanımlayıcı Dizin bitini inceleyerek yönetilen modülleri denetler.</span><span class="sxs-lookup"><span data-stu-id="6056c-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="6056c-119">Bir ayar biti yönetilen bir modülü gösterir.</span><span class="sxs-lookup"><span data-stu-id="6056c-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="6056c-120">Yükleyici yönetilen bir modülü algılarsa, MsCorEE.dll `_CorValidateImage`yükler ve aşağıdaki eylemleri gerçekleştiren çağrıları yapar:</span><span class="sxs-lookup"><span data-stu-id="6056c-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="6056c-121">Görüntünün geçerli bir yönetilen modül olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="6056c-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="6056c-122">Görüntüdeki giriş noktasını ortak dil çalışma zamanındaki (CLR) bir giriş noktasına değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6056c-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="6056c-123">Windows'un 64 bit sürümleri için, BELLEKteki görüntüyü PE32'den PE32+ biçimine dönüştürerek değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6056c-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="6056c-124">Yönetilen modül görüntüleri yüklendiğinde yükleyiciye geri döner.</span><span class="sxs-lookup"><span data-stu-id="6056c-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="6056c-125">Çalıştırılabilir görüntüler için, işletim sistemi yükleyicisi, yürütülebilir de belirtilen giriş noktası ne olursa olsun, [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="6056c-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="6056c-126">DLL montaj görüntüleri için yükleyici [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="6056c-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="6056c-127">`_CorExeMain`veya `_CorDllMain` aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="6056c-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="6056c-128">CLR'yi başharfe iter.</span><span class="sxs-lookup"><span data-stu-id="6056c-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="6056c-129">Derlemenin CLR üstbilgisinden yönetilen giriş noktasını bulur.</span><span class="sxs-lookup"><span data-stu-id="6056c-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="6056c-130">İdam başlar.</span><span class="sxs-lookup"><span data-stu-id="6056c-130">Begins execution.</span></span>  
  
 <span data-ttu-id="6056c-131">Yönetilen modül görüntüleri boşaltıldığında yükleyici [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="6056c-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="6056c-132">Ancak, bu işlev herhangi bir eylem gerçekleştirmez; sadece geri döner.</span><span class="sxs-lookup"><span data-stu-id="6056c-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6056c-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6056c-133">Requirements</span></span>  
 <span data-ttu-id="6056c-134">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6056c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6056c-135">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6056c-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6056c-136">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="6056c-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6056c-137">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6056c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6056c-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6056c-138">See also</span></span>

- [<span data-ttu-id="6056c-139">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6056c-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
