---
title: ICLRDebuggingLibraryProvider::ProvideLibrary Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
ms.openlocfilehash: 8fc2abd0728115edbbfae42958d8013029523ed1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111358"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="591a9-102">ICLRDebuggingLibraryProvider::ProvideLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="591a9-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>

<span data-ttu-id="591a9-103">Ortak dil çalışma zamanı (CLR) sürümüne özel hata ayıklama kitaplıklarının isteğe bağlı olarak bulunmasını ve yüklenmesini sağlayan bir kitaplık sağlayıcısı geri çağırma arabirimi alır.</span><span class="sxs-lookup"><span data-stu-id="591a9-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>

## <a name="syntax"></a><span data-ttu-id="591a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="591a9-104">Syntax</span></span>

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a><span data-ttu-id="591a9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="591a9-105">Parameters</span></span>

`pwszFilename` \
<span data-ttu-id="591a9-106">'ndaki İstenen modülün adı.</span><span class="sxs-lookup"><span data-stu-id="591a9-106">[in] The name of the module being requested.</span></span>

`dwTimestamp` \
<span data-ttu-id="591a9-107">'ndaki PE dosyalarının COFF dosya üstbilgisinde depolanan tarih saat damgası.</span><span class="sxs-lookup"><span data-stu-id="591a9-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>

`pLibraryProvider` \
<span data-ttu-id="591a9-108">'ndaki `SizeOfImage` alanı, PE dosyalarının COFF isteğe bağlı dosya üstbilgisinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="591a9-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>

`hModule` \
<span data-ttu-id="591a9-109">dışı İstenen modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="591a9-109">[out] The handle to the requested module.</span></span>

## <a name="return-value"></a><span data-ttu-id="591a9-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="591a9-110">Return Value</span></span>

<span data-ttu-id="591a9-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="591a9-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="591a9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="591a9-112">HRESULT</span></span>|<span data-ttu-id="591a9-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="591a9-113">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="591a9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="591a9-114">S_OK</span></span>|<span data-ttu-id="591a9-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="591a9-115">The method completed successfully.</span></span>|

## <a name="exceptions"></a><span data-ttu-id="591a9-116">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="591a9-116">Exceptions</span></span>

## <a name="remarks"></a><span data-ttu-id="591a9-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="591a9-117">Remarks</span></span>

<span data-ttu-id="591a9-118">`ProvideLibrary`, hata ayıklayıcının mscordbi. dll ve Mscordacwks. dll gibi belirli CLR dosyalarını ayıklamak için gereken modüller sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="591a9-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="591a9-119">[Ilrdebugging:: CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) yöntemine yapılan bir çağrı, serbest bırakılabileceğini, bu noktada tutamaçları serbest bırakmak için çağıranın sorumluluğunda olduğunu belirten modül tanıtıcılarının geçerli kalması gerekir.</span><span class="sxs-lookup"><span data-stu-id="591a9-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>

<span data-ttu-id="591a9-120">Hata ayıklayıcı, hata ayıklama modülünü bulmak veya temin etmek için kullanılabilir tüm araçları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="591a9-120">The debugger may use any available means to locate or procure the debugging module.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="591a9-121">Bu özellik, API çağıranın yürütülebilir ve olası kötü amaçlı kod içeren modüller sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="591a9-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="591a9-122">Güvenlik önlemi olarak, çağıran, kendisini yürütmek zorunda olmadığı kodu dağıtmak için `ProvideLibrary` kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="591a9-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>
>
> <span data-ttu-id="591a9-123">Mscordbi. dll veya Mscordacwks. dll gibi önceden yayımlanmış bir kitaplıkta önemli bir güvenlik sorunu bulunursa, dolgunun dosyaların bozuk sürümlerini tanıması için düzeltme eki uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="591a9-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="591a9-124">Dolgu daha sonra dosyaların düzeltme eki eklenen sürümleri için istekler verebilir ve herhangi bir isteğe yanıt olarak sağlanmışsa hatalı sürümleri reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="591a9-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="591a9-125">Bu, yalnızca Kullanıcı dolgunun yeni bir sürümüne düzeltme eki uygulanmış olması durumunda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="591a9-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="591a9-126">Düzeltme eki yüklenmemiş sürümler, savunmasız kalacaktır.</span><span class="sxs-lookup"><span data-stu-id="591a9-126">Unpatched versions will remain vulnerable.</span></span>

## <a name="requirements"></a><span data-ttu-id="591a9-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="591a9-127">Requirements</span></span>

<span data-ttu-id="591a9-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="591a9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="591a9-129">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="591a9-129">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="591a9-130">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="591a9-130">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="591a9-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="591a9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="591a9-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="591a9-132">See also</span></span>

- [<span data-ttu-id="591a9-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="591a9-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="591a9-134">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="591a9-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
