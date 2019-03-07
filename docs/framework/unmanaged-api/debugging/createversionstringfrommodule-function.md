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
ms.openlocfilehash: 3ed8b85475dc7327c1aac6f920aba627215e27c7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492029"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="ee004-102">CreateVersionStringFromModule İşlevi</span><span class="sxs-lookup"><span data-stu-id="ee004-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="ee004-103">Hedef işlemdeki ortak dil çalışma zamanı (CLR) yoldan bir sürüm dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ee004-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee004-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee004-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ee004-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee004-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="ee004-106">[in] Hedef CLR yüklendiği işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ee004-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="ee004-107">[in] ' % S'hedef işlemde yüklü CLR tam veya göreli yolu.</span><span class="sxs-lookup"><span data-stu-id="ee004-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="ee004-108">[out] Hedef CLR sürümü dizesi depolamak için dönüş arabelleği.</span><span class="sxs-lookup"><span data-stu-id="ee004-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="ee004-109">[in] Boyutu `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ee004-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="ee004-110">[out] Tarafından döndürülen sürüm dizesinin uzunluğunu `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ee004-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee004-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ee004-111">Return Value</span></span>  
 <span data-ttu-id="ee004-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ee004-112">S_OK</span></span>  
 <span data-ttu-id="ee004-113">Hedef CLR sürümü dizesi başarıyla döndürüldü `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ee004-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="ee004-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ee004-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="ee004-115">`szModuleName` olan null ya da `pBuffer` veya `cchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="ee004-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="ee004-116">`pBuffer` ve `cchBuffer` her ikisi de null veya boş olmayan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ee004-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="ee004-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="ee004-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="ee004-118">`pdwLength` büyüktür `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ee004-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="ee004-119">Her ikisi için null geçtiğinde bu beklenen bir sonucu olabilir `pBuffer` ve `cchBuffer`ve gerekli arabellek boyutu kullanılarak sorgulanabilir `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="ee004-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="ee004-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="ee004-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="ee004-121">`szModuleName` Hedef işlemin içinde geçerli bir CLR yolu içermiyor.</span><span class="sxs-lookup"><span data-stu-id="ee004-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="ee004-122">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="ee004-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ee004-123">`pidDebuggee` Geçerli bir işlem veya diğer hata başvurmuyor.</span><span class="sxs-lookup"><span data-stu-id="ee004-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee004-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee004-124">Remarks</span></span>  
 <span data-ttu-id="ee004-125">Bu işlev tarafından tanımlanan bir CLR işlemi kabul `pidDebuggee` ve tarafından belirtilen bir dize yol `szModuleName`.</span><span class="sxs-lookup"><span data-stu-id="ee004-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="ee004-126">Sürüm dizesi arabellekteki döndürülür, `pBuffer` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="ee004-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="ee004-127">Bu dize işlevi kullanıcı için donuktur; diğer bir deyişle, sürüm dizesindeki iç anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="ee004-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="ee004-128">Bu işlev yalnızca bağlamında kullanılır ve [Createdebuggingınterfacefromversion işlevi](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="ee004-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="ee004-129">Bu işlevin iki kez çağrılması.</span><span class="sxs-lookup"><span data-stu-id="ee004-129">This function should be called twice.</span></span> <span data-ttu-id="ee004-130">İlk kez çağırdığınızda, her ikisi için null değeri geçirmeye `pBuffer` ve `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ee004-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="ee004-131">Bunu yaptığınızda, gerekli arabellek boyutu `pBuffer` içinde döndürülen `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="ee004-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="ee004-132">Ardından, ikinci kez işlevini çağırın ve arabellekteki geçirin `pBuffer` ve boyutunda `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ee004-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee004-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee004-133">Requirements</span></span>  
 <span data-ttu-id="ee004-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee004-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee004-135">**Başlık:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="ee004-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="ee004-136">**Kitaplığı:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="ee004-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="ee004-137">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="ee004-137">**.NET Framework Versions:** 3.5 SP1</span></span>
