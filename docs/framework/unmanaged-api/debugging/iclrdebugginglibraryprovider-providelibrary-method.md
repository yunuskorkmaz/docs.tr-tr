---
description: 'Hakkında daha fazla bilgi edinin: ICLRDebuggingLibraryProvider::P rovideLibrary yöntemi'
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
ms.openlocfilehash: 624061fb9b23af7a69616d4565586ac0fd129860
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772631"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="7a8de-103">ICLRDebuggingLibraryProvider::ProvideLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a8de-103">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>

<span data-ttu-id="7a8de-104">Ortak dil çalışma zamanı (CLR) sürümüne özel hata ayıklama kitaplıklarının isteğe bağlı olarak bulunmasını ve yüklenmesini sağlayan bir kitaplık sağlayıcısı geri çağırma arabirimi alır.</span><span class="sxs-lookup"><span data-stu-id="7a8de-104">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a8de-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a8de-105">Syntax</span></span>

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a><span data-ttu-id="7a8de-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a8de-106">Parameters</span></span>

`pwszFilename` \
<span data-ttu-id="7a8de-107">'ndaki İstenen modülün adı.</span><span class="sxs-lookup"><span data-stu-id="7a8de-107">[in] The name of the module being requested.</span></span>

`dwTimestamp` \
<span data-ttu-id="7a8de-108">'ndaki PE dosyalarının COFF dosya üstbilgisinde depolanan tarih saat damgası.</span><span class="sxs-lookup"><span data-stu-id="7a8de-108">[in] The date time stamp stored in the COFF file header of PE files.</span></span>

`pLibraryProvider` \
<span data-ttu-id="7a8de-109">'ndaki `SizeOfImage` PE DOSYALARıNıN COFF isteğe bağlı dosya üstbilgisinde depolanan alan.</span><span class="sxs-lookup"><span data-stu-id="7a8de-109">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>

`hModule` \
<span data-ttu-id="7a8de-110">dışı İstenen modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="7a8de-110">[out] The handle to the requested module.</span></span>

## <a name="return-value"></a><span data-ttu-id="7a8de-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7a8de-111">Return Value</span></span>

<span data-ttu-id="7a8de-112">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="7a8de-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="7a8de-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7a8de-113">HRESULT</span></span>|<span data-ttu-id="7a8de-114">Description</span><span class="sxs-lookup"><span data-stu-id="7a8de-114">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="7a8de-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a8de-115">S_OK</span></span>|<span data-ttu-id="7a8de-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7a8de-116">The method completed successfully.</span></span>|

## <a name="exceptions"></a><span data-ttu-id="7a8de-117">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="7a8de-117">Exceptions</span></span>

## <a name="remarks"></a><span data-ttu-id="7a8de-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a8de-118">Remarks</span></span>

<span data-ttu-id="7a8de-119">`ProvideLibrary` hata ayıklayıcının, mscordbi.dll ve mscordacwks.dll gibi belirli CLR dosyalarını hata ayıklaması için gereken modüller sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="7a8de-119">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="7a8de-120">[Ilrdebugging:: CanUnloadNow](iclrdebugging-canunloadnow-method.md) yöntemine yapılan bir çağrı, serbest bırakılabileceğini, bu noktada tutamaçları serbest bırakmak için çağıranın sorumluluğunda olduğunu belirten modül tanıtıcılarının geçerli kalması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a8de-120">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>

<span data-ttu-id="7a8de-121">Hata ayıklayıcı, hata ayıklama modülünü bulmak veya temin etmek için kullanılabilir tüm araçları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7a8de-121">The debugger may use any available means to locate or procure the debugging module.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7a8de-122">Bu özellik, API çağıranın yürütülebilir ve olası kötü amaçlı kod içeren modüller sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a8de-122">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="7a8de-123">Güvenlik önlemi olarak çağıran, `ProvideLibrary` kendisini yürütmek zorunda olmadığı kodu dağıtmak için kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="7a8de-123">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>
>
> <span data-ttu-id="7a8de-124">Zaten yayınlanmış bir kitaplıkta mscordbi.dll veya mscordacwks.dll gibi ciddi bir güvenlik sorunu bulunursa, dolgunun dosyaların bozuk sürümlerini tanıması için düzeltme eki uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="7a8de-124">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="7a8de-125">Dolgu daha sonra dosyaların düzeltme eki eklenen sürümleri için istekler verebilir ve herhangi bir isteğe yanıt olarak sağlanmışsa hatalı sürümleri reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="7a8de-125">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="7a8de-126">Bu, yalnızca Kullanıcı dolgunun yeni bir sürümüne düzeltme eki uygulanmış olması durumunda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="7a8de-126">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="7a8de-127">Düzeltme eki yüklenmemiş sürümler, savunmasız kalacaktır.</span><span class="sxs-lookup"><span data-stu-id="7a8de-127">Unpatched versions will remain vulnerable.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a8de-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a8de-128">Requirements</span></span>

<span data-ttu-id="7a8de-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a8de-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="7a8de-130">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7a8de-130">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="7a8de-131">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7a8de-131">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="7a8de-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a8de-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7a8de-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a8de-133">See also</span></span>

- [<span data-ttu-id="7a8de-134">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7a8de-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7a8de-135">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7a8de-135">Debugging</span></span>](index.md)
