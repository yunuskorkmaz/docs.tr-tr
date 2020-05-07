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
ms.openlocfilehash: 7bbb49dc6ee9b1d29dd61ccdcfdacb62740133ed
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860271"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="c142b-102">ICLRDebuggingLibraryProvider::ProvideLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c142b-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>

<span data-ttu-id="c142b-103">Ortak dil çalışma zamanı (CLR) sürümüne özel hata ayıklama kitaplıklarının isteğe bağlı olarak bulunmasını ve yüklenmesini sağlayan bir kitaplık sağlayıcısı geri çağırma arabirimi alır.</span><span class="sxs-lookup"><span data-stu-id="c142b-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>

## <a name="syntax"></a><span data-ttu-id="c142b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c142b-104">Syntax</span></span>

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a><span data-ttu-id="c142b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c142b-105">Parameters</span></span>

`pwszFilename` \
<span data-ttu-id="c142b-106">'ndaki İstenen modülün adı.</span><span class="sxs-lookup"><span data-stu-id="c142b-106">[in] The name of the module being requested.</span></span>

`dwTimestamp` \
<span data-ttu-id="c142b-107">'ndaki PE dosyalarının COFF dosya üstbilgisinde depolanan tarih saat damgası.</span><span class="sxs-lookup"><span data-stu-id="c142b-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>

`pLibraryProvider` \
<span data-ttu-id="c142b-108">'ndaki PE `SizeOfImage` dosyalarının COFF isteğe bağlı dosya üstbilgisinde depolanan alan.</span><span class="sxs-lookup"><span data-stu-id="c142b-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>

`hModule` \
<span data-ttu-id="c142b-109">dışı İstenen modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="c142b-109">[out] The handle to the requested module.</span></span>

## <a name="return-value"></a><span data-ttu-id="c142b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c142b-110">Return Value</span></span>

<span data-ttu-id="c142b-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="c142b-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="c142b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c142b-112">HRESULT</span></span>|<span data-ttu-id="c142b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c142b-113">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="c142b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c142b-114">S_OK</span></span>|<span data-ttu-id="c142b-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c142b-115">The method completed successfully.</span></span>|

## <a name="exceptions"></a><span data-ttu-id="c142b-116">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="c142b-116">Exceptions</span></span>

## <a name="remarks"></a><span data-ttu-id="c142b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c142b-117">Remarks</span></span>

<span data-ttu-id="c142b-118">`ProvideLibrary`hata ayıklayıcının mscordbi. dll ve Mscordacwks. dll gibi belirli CLR dosyalarını ayıklamak için gereken modüller sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="c142b-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="c142b-119">[Ilrdebugging:: CanUnloadNow](iclrdebugging-canunloadnow-method.md) yöntemine yapılan bir çağrı, serbest bırakılabileceğini, bu noktada tutamaçları serbest bırakmak için çağıranın sorumluluğunda olduğunu belirten modül tanıtıcılarının geçerli kalması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c142b-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>

<span data-ttu-id="c142b-120">Hata ayıklayıcı, hata ayıklama modülünü bulmak veya temin etmek için kullanılabilir tüm araçları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c142b-120">The debugger may use any available means to locate or procure the debugging module.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c142b-121">Bu özellik, API çağıranın yürütülebilir ve olası kötü amaçlı kod içeren modüller sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c142b-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="c142b-122">Güvenlik önlemi olarak çağıran, kendisini yürütmek zorunda olmadığı kodu `ProvideLibrary` dağıtmak için kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="c142b-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>
>
> <span data-ttu-id="c142b-123">Mscordbi. dll veya Mscordacwks. dll gibi önceden yayımlanmış bir kitaplıkta önemli bir güvenlik sorunu bulunursa, dolgunun dosyaların bozuk sürümlerini tanıması için düzeltme eki uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c142b-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="c142b-124">Dolgu daha sonra dosyaların düzeltme eki eklenen sürümleri için istekler verebilir ve herhangi bir isteğe yanıt olarak sağlanmışsa hatalı sürümleri reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="c142b-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="c142b-125">Bu, yalnızca Kullanıcı dolgunun yeni bir sürümüne düzeltme eki uygulanmış olması durumunda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="c142b-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="c142b-126">Düzeltme eki yüklenmemiş sürümler, savunmasız kalacaktır.</span><span class="sxs-lookup"><span data-stu-id="c142b-126">Unpatched versions will remain vulnerable.</span></span>

## <a name="requirements"></a><span data-ttu-id="c142b-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c142b-127">Requirements</span></span>

<span data-ttu-id="c142b-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c142b-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="c142b-129">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c142b-129">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="c142b-130">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c142b-130">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c142b-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c142b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c142b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c142b-132">See also</span></span>

- [<span data-ttu-id="c142b-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c142b-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c142b-134">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c142b-134">Debugging</span></span>](index.md)
