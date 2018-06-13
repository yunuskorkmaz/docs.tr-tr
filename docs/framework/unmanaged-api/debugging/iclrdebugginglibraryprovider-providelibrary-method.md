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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0644258eb1622f388f55d0657c8922079fe4dc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407254"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="ba1b7-102">ICLRDebuggingLibraryProvider::ProvideLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba1b7-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>
<span data-ttu-id="ba1b7-103">Ortak dil çalışma zamanı (CLR) sürüme özgü hata ayıklama kitaplıkları bulunduğu ve yüklenen üzerinde isteğe bağlı olarak geri çağırma arabirimi kitaplığı sağlayıcısı alır.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba1b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba1b7-104">Syntax</span></span>  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba1b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba1b7-105">Parameters</span></span>  
 `pwszFilename`  
 <span data-ttu-id="ba1b7-106">[in] İstenen modülü adı.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-106">[in] The name of the module being requested .</span></span>  
  
 `dwTimestamp`  
 <span data-ttu-id="ba1b7-107">[in] PE dosyaları COFF dosya üstbilgisinde saklanan tarih ve saat damgası.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="ba1b7-108">[in] `SizeOfImage` PE dosyaları COFF isteğe bağlı bir dosya üstbilgisinde saklanan alan.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>  
  
 `hModule`  
 <span data-ttu-id="ba1b7-109">[out] İstenen modülü için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-109">[out] The handle to the requested module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba1b7-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ba1b7-110">Return Value</span></span>  
 <span data-ttu-id="ba1b7-111">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ba1b7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ba1b7-112">HRESULT</span></span>|<span data-ttu-id="ba1b7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba1b7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ba1b7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ba1b7-114">S_OK</span></span>|<span data-ttu-id="ba1b7-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-115">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ba1b7-116">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="ba1b7-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba1b7-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba1b7-117">Remarks</span></span>  
 <span data-ttu-id="ba1b7-118">`ProvideLibrary` hata ayıklama mscordbi.dll ve Mscordacwks.dll dosyasının gibi belirli CLR dosyaları için gerekli olan modülleri sağlamak hata ayıklayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="ba1b7-119">Modül tanıtıcıları yapılan bir çağrı kadar geçerli kalır zorunda [Iclrdebugging::canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) yöntemi gösterir boşaltılması, bu noktada, tanıtıcıları serbest yapanın sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>  
  
 <span data-ttu-id="ba1b7-120">Hata ayıklayıcı bulun veya hata ayıklama modülü tedarik etmek için herhangi bir kullanılabilir yöntem kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-120">The debugger may use any available means to locate or procure the debugging module.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba1b7-121">Bu özellik yürütülebilir ve büyük olasılıkla kötü amaçlı kod içeren modüller sağlamak API çağıran sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="ba1b7-122">Bir güvenlik önlemi olarak çağıran değil kullanması gereken `ProvideLibrary` kendisini yürütmek hazır değil, herhangi bir kod dağıtmak için.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>  
>   
>  <span data-ttu-id="ba1b7-123">Örneğin mscordbi.dll veya Mscordacwks.dll dosyasının, önceden yayımlanmış bir Kitaplığı'nda ciddi güvenlik sorunu bulunup dolgu dosyalarının hatalı sürümleri tanımak için düzeltme eki.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="ba1b7-124">Dolgu sonra düzeltme eki dosyalarının sürümleri için istekleri ve herhangi isteğine yanıt olarak sağlandıysa hatalı sürümleri reddedin.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="ba1b7-125">Yalnızca kullanıcı dolgu yeni bir sürüme düzeltme eki uygulandı bu durum ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="ba1b7-126">Düzeltme eki yüklenmemiş sürümleri açık halde kalır.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-126">Unpatched versions will remain vulnerable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba1b7-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba1b7-127">Requirements</span></span>  
 <span data-ttu-id="ba1b7-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba1b7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba1b7-129">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba1b7-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba1b7-130">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba1b7-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba1b7-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba1b7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba1b7-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba1b7-132">See Also</span></span>  
 [<span data-ttu-id="ba1b7-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ba1b7-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ba1b7-134">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ba1b7-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
