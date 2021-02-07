---
description: 'Daha fazla bilgi edinin: CreateVersionStringFromModule Işlevi'
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
ms.openlocfilehash: 45ae3ec31cf77e4c96e42a58b23e1f52dcf7c54b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661551"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="bed85-103">CreateVersionStringFromModule İşlevi</span><span class="sxs-lookup"><span data-stu-id="bed85-103">CreateVersionStringFromModule Function</span></span>

<span data-ttu-id="bed85-104">Hedef işlemdeki ortak dil çalışma zamanı (CLR) yolundan bir sürüm dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bed85-104">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bed85-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bed85-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bed85-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bed85-106">Parameters</span></span>  

 `pidDebuggee`  
 <span data-ttu-id="bed85-107">'ndaki Hedef CLR 'nin yüklendiği işlemin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="bed85-107">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="bed85-108">'ndaki İşlemde yüklü olan hedef CLR 'ye tam veya göreli yol.</span><span class="sxs-lookup"><span data-stu-id="bed85-108">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="bed85-109">dışı Hedef CLR için sürüm dizesini depolamak için dönüş arabelleği.</span><span class="sxs-lookup"><span data-stu-id="bed85-109">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="bed85-110">'ndaki Boyut `pBuffer` .</span><span class="sxs-lookup"><span data-stu-id="bed85-110">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="bed85-111">dışı Tarafından döndürülen sürüm dizesinin uzunluğu `pBuffer` .</span><span class="sxs-lookup"><span data-stu-id="bed85-111">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bed85-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bed85-112">Return Value</span></span>  

 <span data-ttu-id="bed85-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="bed85-113">S_OK</span></span>  
 <span data-ttu-id="bed85-114">Hedef CLR 'nin sürüm dizesi içinde başarıyla döndürüldü `pBuffer` .</span><span class="sxs-lookup"><span data-stu-id="bed85-114">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="bed85-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bed85-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="bed85-116">`szModuleName` null veya ya da `pBuffer` `cchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="bed85-116">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="bed85-117">`pBuffer` ve `cchBuffer` her ikisi de null ya da boş olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bed85-117">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="bed85-118">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="bed85-118">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="bed85-119">`pdwLength` Şundan büyüktür `cchBuffer` .</span><span class="sxs-lookup"><span data-stu-id="bed85-119">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="bed85-120">Hem hem de için null değeri geçirtiyse `pBuffer` `cchBuffer` ve gereken arabellek boyutunu kullanarak sorguladıysanız, bu beklenen bir sonuç olabilir `pdwLength` .</span><span class="sxs-lookup"><span data-stu-id="bed85-120">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="bed85-121">HRESULT_FROM_WIN32 (ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="bed85-121">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="bed85-122">`szModuleName` Hedef işlemde geçerli bir CLR yolu içermiyor.</span><span class="sxs-lookup"><span data-stu-id="bed85-122">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="bed85-123">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="bed85-123">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="bed85-124">`pidDebuggee` geçerli bir işleme ya da başka bir hataya başvurmaz.</span><span class="sxs-lookup"><span data-stu-id="bed85-124">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bed85-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bed85-125">Remarks</span></span>  

 <span data-ttu-id="bed85-126">Bu işlev tarafından tanımlanan bir CLR işlemini `pidDebuggee` ve tarafından belirtilen bir dize yolunu kabul eder `szModuleName` .</span><span class="sxs-lookup"><span data-stu-id="bed85-126">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="bed85-127">Sürüm dizesi, işaret eden arabellekte döndürülür `pBuffer` .</span><span class="sxs-lookup"><span data-stu-id="bed85-127">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="bed85-128">Bu dize, işlev kullanıcısının opaktır; Yani, sürüm dizesinde hiç iç anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="bed85-128">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="bed85-129">Yalnızca bu işlev bağlamında ve [CreateDebuggingInterfaceFromVersion İşlevi](createdebugginginterfacefromversion-function-for-silverlight.md)için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bed85-129">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="bed85-130">Bu işlev iki kez çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bed85-130">This function should be called twice.</span></span> <span data-ttu-id="bed85-131">İlk kez çağırdığınızda, hem hem de için null değeri geçirin `pBuffer` `cchBuffer` .</span><span class="sxs-lookup"><span data-stu-id="bed85-131">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="bed85-132">Bunu yaptığınızda, için gereken arabelleğin boyutu `pBuffer` ' de döndürülür `pdwLength` .</span><span class="sxs-lookup"><span data-stu-id="bed85-132">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="bed85-133">Daha sonra işlevi ikinci bir kez çağırabilir ve içindeki arabelleği `pBuffer` ve boyutuna geçirebilirsiniz `cchBuffer` .</span><span class="sxs-lookup"><span data-stu-id="bed85-133">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bed85-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bed85-134">Requirements</span></span>  

 <span data-ttu-id="bed85-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bed85-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bed85-136">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="bed85-136">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="bed85-137">**Kitaplık:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="bed85-137">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="bed85-138">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="bed85-138">**.NET Framework Versions:** 3.5 SP1</span></span>
