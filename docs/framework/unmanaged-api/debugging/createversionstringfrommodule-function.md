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
ms.openlocfilehash: 1b944034251b34350057866b2a52e63e934d72d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733353"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="8f727-102">CreateVersionStringFromModule İşlevi</span><span class="sxs-lookup"><span data-stu-id="8f727-102">CreateVersionStringFromModule Function</span></span>

<span data-ttu-id="8f727-103">Hedef işlemdeki ortak dil çalışma zamanı (CLR) yolundan bir sürüm dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f727-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f727-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8f727-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f727-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f727-105">Parameters</span></span>  

 `pidDebuggee`  
 <span data-ttu-id="8f727-106">'ndaki Hedef CLR 'nin yüklendiği işlemin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="8f727-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="8f727-107">'ndaki İşlemde yüklü olan hedef CLR 'ye tam veya göreli yol.</span><span class="sxs-lookup"><span data-stu-id="8f727-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="8f727-108">dışı Hedef CLR için sürüm dizesini depolamak için dönüş arabelleği.</span><span class="sxs-lookup"><span data-stu-id="8f727-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="8f727-109">'ndaki Boyut `pBuffer` .</span><span class="sxs-lookup"><span data-stu-id="8f727-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="8f727-110">dışı Tarafından döndürülen sürüm dizesinin uzunluğu `pBuffer` .</span><span class="sxs-lookup"><span data-stu-id="8f727-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f727-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f727-111">Return Value</span></span>  

 <span data-ttu-id="8f727-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f727-112">S_OK</span></span>  
 <span data-ttu-id="8f727-113">Hedef CLR 'nin sürüm dizesi içinde başarıyla döndürüldü `pBuffer` .</span><span class="sxs-lookup"><span data-stu-id="8f727-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="8f727-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8f727-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="8f727-115">`szModuleName` null veya ya da `pBuffer` `cchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="8f727-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="8f727-116">`pBuffer` ve `cchBuffer` her ikisi de null ya da boş olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f727-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="8f727-117">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="8f727-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="8f727-118">`pdwLength` Şundan büyüktür `cchBuffer` .</span><span class="sxs-lookup"><span data-stu-id="8f727-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="8f727-119">Hem hem de için null değeri geçirtiyse `pBuffer` `cchBuffer` ve gereken arabellek boyutunu kullanarak sorguladıysanız, bu beklenen bir sonuç olabilir `pdwLength` .</span><span class="sxs-lookup"><span data-stu-id="8f727-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="8f727-120">HRESULT_FROM_WIN32 (ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="8f727-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="8f727-121">`szModuleName` Hedef işlemde geçerli bir CLR yolu içermiyor.</span><span class="sxs-lookup"><span data-stu-id="8f727-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="8f727-122">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="8f727-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="8f727-123">`pidDebuggee` geçerli bir işleme ya da başka bir hataya başvurmaz.</span><span class="sxs-lookup"><span data-stu-id="8f727-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f727-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f727-124">Remarks</span></span>  

 <span data-ttu-id="8f727-125">Bu işlev tarafından tanımlanan bir CLR işlemini `pidDebuggee` ve tarafından belirtilen bir dize yolunu kabul eder `szModuleName` .</span><span class="sxs-lookup"><span data-stu-id="8f727-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="8f727-126">Sürüm dizesi, işaret eden arabellekte döndürülür `pBuffer` .</span><span class="sxs-lookup"><span data-stu-id="8f727-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="8f727-127">Bu dize, işlev kullanıcısının opaktır; Yani, sürüm dizesinde hiç iç anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="8f727-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="8f727-128">Yalnızca bu işlev bağlamında ve [CreateDebuggingInterfaceFromVersion İşlevi](createdebugginginterfacefromversion-function-for-silverlight.md)için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f727-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="8f727-129">Bu işlev iki kez çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f727-129">This function should be called twice.</span></span> <span data-ttu-id="8f727-130">İlk kez çağırdığınızda, hem hem de için null değeri geçirin `pBuffer` `cchBuffer` .</span><span class="sxs-lookup"><span data-stu-id="8f727-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="8f727-131">Bunu yaptığınızda, için gereken arabelleğin boyutu `pBuffer` ' de döndürülür `pdwLength` .</span><span class="sxs-lookup"><span data-stu-id="8f727-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="8f727-132">Daha sonra işlevi ikinci bir kez çağırabilir ve içindeki arabelleği `pBuffer` ve boyutuna geçirebilirsiniz `cchBuffer` .</span><span class="sxs-lookup"><span data-stu-id="8f727-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f727-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f727-133">Requirements</span></span>  

 <span data-ttu-id="8f727-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f727-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f727-135">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="8f727-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="8f727-136">**Kitaplık:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="8f727-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="8f727-137">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="8f727-137">**.NET Framework Versions:** 3.5 SP1</span></span>
