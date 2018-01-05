---
title: "EnumerateCLRs İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EnumerateCLRs
api_location: dbgshim.dll
api_type: COM
f1_keywords: EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6539b471d6a3075bb4cec69b382cf7702a439d5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="19fb3-102">EnumerateCLRs İşlevi</span><span class="sxs-lookup"><span data-stu-id="19fb3-102">EnumerateCLRs Function</span></span>
<span data-ttu-id="19fb3-103">Bir işlemde CLRs numaralandırma için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="19fb3-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19fb3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19fb3-104">Syntax</span></span>  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19fb3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19fb3-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="19fb3-106">[in] Yüklenen CLRs Numaralandırılacak işleminin işlem tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="19fb3-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="19fb3-107">[out] Bir CLR başlatma devam etmek için kullanılan olay tanıtıcıları içeren bir dizi işaretçi.</span><span class="sxs-lookup"><span data-stu-id="19fb3-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="19fb3-108">Dizideki her tanıtıcı geçerli olması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="19fb3-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="19fb3-109">Geçerli işleme devam başlangıç olayı olarak aynı dizinde bulunan karşılık gelen çalışma zamanı için kullanılmak üzere olup olmadığını `ppStringArrayOut`.</span><span class="sxs-lookup"><span data-stu-id="19fb3-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="19fb3-110">[out] CLRs tam yollarını belirtin bir dizeler dizisi işaretçisine işlemde yüklü.</span><span class="sxs-lookup"><span data-stu-id="19fb3-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="19fb3-111">[out] İşaretçi eşit boyutta uzunluğunu içeren DWORD `ppHandleArrayOut` ve `pdwArrayLengthOut`.</span><span class="sxs-lookup"><span data-stu-id="19fb3-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19fb3-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="19fb3-112">Return Value</span></span>  
 <span data-ttu-id="19fb3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="19fb3-113">S_OK</span></span>  
 <span data-ttu-id="19fb3-114">İşlem CLRs sayısında başarıyla belirlendi ve karşılık gelen tanıtıcısı ve yol dizileri düzgün doldurulmuş.</span><span class="sxs-lookup"><span data-stu-id="19fb3-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="19fb3-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="19fb3-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="19fb3-116">Ya da `ppHandleArrayOut` veya `ppStringArrayOut` null, veya `pdwArrayLengthOut` null.</span><span class="sxs-lookup"><span data-stu-id="19fb3-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="19fb3-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="19fb3-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="19fb3-118">İşlev işleyici ve yol diziler için yeterli bellek ayıramıyor.</span><span class="sxs-lookup"><span data-stu-id="19fb3-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="19fb3-119">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="19fb3-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="19fb3-120">Yüklenen CLRs numaralandırılamadı.</span><span class="sxs-lookup"><span data-stu-id="19fb3-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19fb3-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19fb3-121">Remarks</span></span>  
 <span data-ttu-id="19fb3-122">Tarafından tanımlanan bir hedef işleminin `debuggeePID`, işlevi yolları, bir dizi döndürür `ppStringArrayOut`, işlemde yüklü CLRs; bir dizi olay işleyicilerini `ppHandleArrayOut`, hangi içerebilir devam startup olayı aynı dizinde; CLR için ve diziler boyutunu `pdwArrayLengthOut`, yüklenen CLRs sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="19fb3-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="19fb3-123">Windows işletim sisteminde `debuggeePID` eşlemeleri bir işletim sistemi için işlem tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="19fb3-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="19fb3-124">Bellek için `ppHandleArrayOut` ve `ppStringArrayOut` bu işlev tarafından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="19fb3-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="19fb3-125">Ayrılan bellek boşaltmak için çağırmalısınız [CloseCLREnumeration işlevi](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span><span class="sxs-lookup"><span data-stu-id="19fb3-125">To free the memory allocated, you must call [CloseCLREnumeration Function](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="19fb3-126">Bu işlev hedef işleminde CLRs sayısını döndürmek için sıfıra ayarlayın dizi parametrelerinin her ikisini de ile çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="19fb3-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="19fb3-127">Bu sayı çağıran oluşturulacak arabellek boyutu çıkarımını: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span><span class="sxs-lookup"><span data-stu-id="19fb3-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19fb3-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19fb3-128">Requirements</span></span>  
 <span data-ttu-id="19fb3-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19fb3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19fb3-130">**Başlık:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="19fb3-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="19fb3-131">**Kitaplığı:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="19fb3-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="19fb3-132">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="19fb3-132">**.NET Framework Versions:** 3.5 SP1</span></span>
