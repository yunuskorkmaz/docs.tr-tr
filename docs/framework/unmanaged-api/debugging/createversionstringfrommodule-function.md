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
ms.openlocfilehash: 60b7d77542a5065fb1e09a98e659cac17fb093e9
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860856"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="d9720-102">CreateVersionStringFromModule İşlevi</span><span class="sxs-lookup"><span data-stu-id="d9720-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="d9720-103">Hedef işlemdeki ortak dil çalışma zamanı (CLR) yolundan bir sürüm dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9720-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9720-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9720-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d9720-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9720-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="d9720-106">'ndaki Hedef CLR 'nin yüklendiği işlemin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d9720-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="d9720-107">'ndaki İşlemde yüklü olan hedef CLR 'ye tam veya göreli yol.</span><span class="sxs-lookup"><span data-stu-id="d9720-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="d9720-108">dışı Hedef CLR için sürüm dizesini depolamak için dönüş arabelleği.</span><span class="sxs-lookup"><span data-stu-id="d9720-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="d9720-109">'ndaki Boyut `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d9720-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="d9720-110">dışı Tarafından `pBuffer`döndürülen sürüm dizesinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="d9720-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9720-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9720-111">Return Value</span></span>  
 <span data-ttu-id="d9720-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9720-112">S_OK</span></span>  
 <span data-ttu-id="d9720-113">Hedef CLR 'nin sürüm dizesi içinde `pBuffer`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d9720-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="d9720-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d9720-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="d9720-115">`szModuleName`null veya ya da `pBuffer` `cchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="d9720-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="d9720-116">`pBuffer`ve `cchBuffer` her ikisi de null ya da boş olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9720-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="d9720-117">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="d9720-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="d9720-118">`pdwLength`Şundan `cchBuffer`büyüktür.</span><span class="sxs-lookup"><span data-stu-id="d9720-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="d9720-119">Hem hem de `pBuffer` için null değeri geçirtiyse ve gereken arabellek boyutunu kullanarak `cchBuffer` `pdwLength`sorguladıysanız, bu beklenen bir sonuç olabilir.</span><span class="sxs-lookup"><span data-stu-id="d9720-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="d9720-120">HRESULT_FROM_WIN32 (ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="d9720-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="d9720-121">`szModuleName`Hedef işlemde geçerli bir CLR yolu içermiyor.</span><span class="sxs-lookup"><span data-stu-id="d9720-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="d9720-122">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="d9720-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="d9720-123">`pidDebuggee`geçerli bir işleme ya da başka bir hataya başvurmaz.</span><span class="sxs-lookup"><span data-stu-id="d9720-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9720-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9720-124">Remarks</span></span>  
 <span data-ttu-id="d9720-125">Bu işlev tarafından `pidDebuggee` tanımlanan bir clr işlemini ve tarafından `szModuleName`belirtilen bir dize yolunu kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d9720-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="d9720-126">Sürüm dizesi, işaret eden `pBuffer` arabellekte döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d9720-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="d9720-127">Bu dize, işlev kullanıcısının opaktır; Yani, sürüm dizesinde hiç iç anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="d9720-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="d9720-128">Yalnızca bu işlev bağlamında ve [CreateDebuggingInterfaceFromVersion İşlevi](createdebugginginterfacefromversion-function-for-silverlight.md)için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9720-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="d9720-129">Bu işlev iki kez çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9720-129">This function should be called twice.</span></span> <span data-ttu-id="d9720-130">İlk kez çağırdığınızda, hem hem de `pBuffer` için null değeri geçirin. `cchBuffer`</span><span class="sxs-lookup"><span data-stu-id="d9720-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="d9720-131">Bunu yaptığınızda, için `pBuffer` gereken arabelleğin boyutu ' de `pdwLength`döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d9720-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="d9720-132">Daha sonra işlevi ikinci bir kez çağırabilir ve içindeki arabelleği `pBuffer` ve boyutuna geçirebilirsiniz. `cchBuffer`</span><span class="sxs-lookup"><span data-stu-id="d9720-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9720-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9720-133">Requirements</span></span>  
 <span data-ttu-id="d9720-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9720-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9720-135">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="d9720-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="d9720-136">**Kitaplık:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="d9720-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="d9720-137">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="d9720-137">**.NET Framework Versions:** 3.5 SP1</span></span>
