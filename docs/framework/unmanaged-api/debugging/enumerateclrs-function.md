---
title: EnumerateCLRs İşlevi
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7532218728aead72186b5156da87db6d3bc0a8c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469345"
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="9cf82-102">EnumerateCLRs İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cf82-102">EnumerateCLRs Function</span></span>
<span data-ttu-id="9cf82-103">Bir işlemde CLRs numaralandırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cf82-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cf82-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9cf82-104">Syntax</span></span>  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cf82-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9cf82-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="9cf82-106">[in] Yüklenen CLRs Numaralandırılacak işleminin işlem tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="9cf82-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="9cf82-107">[out] CLR başlangıç devam etmek için kullanılan olay tanıtıcıları içeren bir dizi için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9cf82-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="9cf82-108">Dizideki her tutamacı geçerli olması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="9cf82-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="9cf82-109">Geçerli tanıtıcı devam başlangıç olayı olarak aynı dizinde bulunan karşılık gelen çalışma zamanı için kullanılmak üzere olup olmadığını `ppStringArrayOut`.</span><span class="sxs-lookup"><span data-stu-id="9cf82-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="9cf82-110">[out] Tam yolları CLRs belirten bir dize dizisi işaretçisine işlemde yüklü.</span><span class="sxs-lookup"><span data-stu-id="9cf82-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="9cf82-111">[out] İşaretçisine eşit boyutlu uzunluğunu içeren bir DWORD `ppHandleArrayOut` ve `pdwArrayLengthOut`.</span><span class="sxs-lookup"><span data-stu-id="9cf82-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cf82-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9cf82-112">Return Value</span></span>  
 <span data-ttu-id="9cf82-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9cf82-113">S_OK</span></span>  
 <span data-ttu-id="9cf82-114">İşlem CLRs sayısında başarıyla belirlendi ve karşılık gelen tanıtıcısı ve yol diziler düzgün doldurulmuş.</span><span class="sxs-lookup"><span data-stu-id="9cf82-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="9cf82-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9cf82-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="9cf82-116">Ya da `ppHandleArrayOut` veya `ppStringArrayOut` null ise veya `pdwArrayLengthOut` null.</span><span class="sxs-lookup"><span data-stu-id="9cf82-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="9cf82-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9cf82-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="9cf82-118">İşlev tanıtıcısı ve yol diziler için yeterli bellek ayıramadı.</span><span class="sxs-lookup"><span data-stu-id="9cf82-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="9cf82-119">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="9cf82-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="9cf82-120">Yüklenen CLRs numaralandırılamadı.</span><span class="sxs-lookup"><span data-stu-id="9cf82-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cf82-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9cf82-121">Remarks</span></span>  
 <span data-ttu-id="9cf82-122">Tarafından tanımlanan bir hedef işlemi `debuggeePID`, işlev yolları, bir dizi döndürür `ppStringArrayOut`, işlemde yüklü CLRs; bir dizi olay işleyicilerini `ppHandleArrayOut`, hangi içerebilir devam başlangıç olay için aynı dizindeki; CLR ve dizi boyutu `pdwArrayLengthOut`, yüklenen CLRs sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cf82-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="9cf82-123">Windows işletim sisteminde `debuggeePID` eşlemeleri bir işletim sistemi için işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9cf82-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="9cf82-124">Bellek için `ppHandleArrayOut` ve `ppStringArrayOut` bu işlev tarafından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="9cf82-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="9cf82-125">Ayrılan bellek boşaltmak için çağırmalısınız [CloseCLREnumeration işlevi](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span><span class="sxs-lookup"><span data-stu-id="9cf82-125">To free the memory allocated, you must call [CloseCLREnumeration Function](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="9cf82-126">Bu işlev, her iki dizi parametrelerle hedef işlemde CLRs sayısını döndürmek için null olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="9cf82-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="9cf82-127">Bu sayıdan, bir çağıranın oluşturulacak arabellek boyutu çıkarabilir: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span><span class="sxs-lookup"><span data-stu-id="9cf82-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cf82-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9cf82-128">Requirements</span></span>  
 <span data-ttu-id="9cf82-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cf82-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cf82-130">**Başlık:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="9cf82-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="9cf82-131">**Kitaplığı:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="9cf82-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="9cf82-132">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="9cf82-132">**.NET Framework Versions:** 3.5 SP1</span></span>
