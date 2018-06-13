---
title: CreateVersionStringFromModule İşlevi
ms.date: 03/30/2017
api_name:
- CreateVersionStringFromModule
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0988b2c4471cb5449f7c7fac82c6e94bcd537b7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409286"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="6bda2-102">CreateVersionStringFromModule İşlevi</span><span class="sxs-lookup"><span data-stu-id="6bda2-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="6bda2-103">Ortak dil çalışma zamanı (CLR) yolu bir hedef işlemde bir sürüm dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6bda2-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bda2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bda2-104">Syntax</span></span>  
  
```  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6bda2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6bda2-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="6bda2-106">[in] CLR hedef yüklendiği işlem tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="6bda2-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="6bda2-107">[in] İşlemde yüklü CLR hedef tam veya göreli yolu.</span><span class="sxs-lookup"><span data-stu-id="6bda2-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="6bda2-108">[out] Hedef CLR sürüm dizesi depolamak için arabellek döndür.</span><span class="sxs-lookup"><span data-stu-id="6bda2-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="6bda2-109">[in] Boyutunu `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="6bda2-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="6bda2-110">[out] Tarafından döndürülen sürüm dizesi `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="6bda2-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bda2-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6bda2-111">Return Value</span></span>  
 <span data-ttu-id="6bda2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6bda2-112">S_OK</span></span>  
 <span data-ttu-id="6bda2-113">Hedef CLR sürüm dizesi başarıyla döndürüldü `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="6bda2-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="6bda2-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6bda2-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="6bda2-115">`szModuleName` olan null ya da `pBuffer` veya `cchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="6bda2-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="6bda2-116">`pBuffer` ve `cchBuffer` her ikisi de null veya boş olmayan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6bda2-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="6bda2-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="6bda2-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="6bda2-118">`pdwLength` Daha fazla `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="6bda2-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="6bda2-119">Her ikisi için null geçtiğinde, bu beklenen bir sonucu olabilir `pBuffer` ve `cchBuffer`ve gerekli arabellek boyutu kullanarak sorgulanan `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="6bda2-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="6bda2-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="6bda2-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="6bda2-121">`szModuleName` Hedef işlemin geçerli bir CLR yoluna sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6bda2-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="6bda2-122">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="6bda2-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="6bda2-123">`pidDebuggee` Geçerli bir işlem veya diğer hata başvurmuyor.</span><span class="sxs-lookup"><span data-stu-id="6bda2-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bda2-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bda2-124">Remarks</span></span>  
 <span data-ttu-id="6bda2-125">Bu işlev tarafından tanımlanan bir CLR işlem kabul `pidDebuggee` tarafından belirtilen bir dize yol `szModuleName`.</span><span class="sxs-lookup"><span data-stu-id="6bda2-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="6bda2-126">Sürüm dizesi arabellekte döndürülür, `pBuffer` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6bda2-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="6bda2-127">Bu dize işlevi kullanıcıya donuk; diğer bir deyişle, sürüm dizesindeki iç hiçbir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="6bda2-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="6bda2-128">Yalnızca bu işlev bağlamda kullanılır ve [Createdebuggingınterfacefromversion işlevi](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="6bda2-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="6bda2-129">Bu işlev iki kez çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6bda2-129">This function should be called twice.</span></span> <span data-ttu-id="6bda2-130">İlk kez çağırdığınızda, her ikisi için null geçirmeniz `pBuffer` ve `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="6bda2-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="6bda2-131">Bunu yaptığınızda, gerekli arabellek boyutu `pBuffer` içinde döndürülen `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="6bda2-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="6bda2-132">Ardından, ikinci kez işlevini çağırın ve arabellekte geçirin `pBuffer` ve boyutunda `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="6bda2-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bda2-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bda2-133">Requirements</span></span>  
 <span data-ttu-id="6bda2-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bda2-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bda2-135">**Başlık:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="6bda2-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="6bda2-136">**Kitaplığı:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="6bda2-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="6bda2-137">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="6bda2-137">**.NET Framework Versions:** 3.5 SP1</span></span>
