---
description: ': EnumerateCLRs Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 75124ef1e1e8588cb3d709161c3c1119e960be9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637793"
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="1a9ad-103">EnumerateCLRs İşlevi</span><span class="sxs-lookup"><span data-stu-id="1a9ad-103">EnumerateCLRs Function</span></span>

<span data-ttu-id="1a9ad-104">Bir işlemdeki CLRs 'yi listelemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-104">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a9ad-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a9ad-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a9ad-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a9ad-106">Parameters</span></span>  

 `debuggeePID`  
 <span data-ttu-id="1a9ad-107">'ndaki Yüklenen CLRs 'nin numaralandıralınacağı işlemin işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-107">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="1a9ad-108">dışı CLR başlatmaya devam etmek için kullanılan olay tutamaçlarını içeren bir diziye yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-108">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="1a9ad-109">Dizideki her tanıtıcının geçerli olması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-109">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="1a9ad-110">Geçerliyse, tanıtıcı aynı dizininde bulunan ilgili çalışma zamanı için devam-başlatma olayı olarak kullanılır `ppStringArrayOut` .</span><span class="sxs-lookup"><span data-stu-id="1a9ad-110">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="1a9ad-111">dışı İşlemde yüklü olan tüm CLRs yollarını belirten dizeler dizisine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-111">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="1a9ad-112">dışı Eşit büyüklükte boyut ve uzunluğu içeren bir DWORD işaretçisi `ppHandleArrayOut` `pdwArrayLengthOut` .</span><span class="sxs-lookup"><span data-stu-id="1a9ad-112">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a9ad-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1a9ad-113">Return Value</span></span>  

 <span data-ttu-id="1a9ad-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a9ad-114">S_OK</span></span>  
 <span data-ttu-id="1a9ad-115">İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-115">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="1a9ad-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1a9ad-116">E_INVALIDARG</span></span>  
 <span data-ttu-id="1a9ad-117">Ya da null ya da `ppHandleArrayOut` `ppStringArrayOut` `pdwArrayLengthOut` null.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-117">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="1a9ad-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1a9ad-118">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="1a9ad-119">İşlev, tanıtıcı ve yol dizileri için yeterli bellek ayıramadı.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-119">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="1a9ad-120">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="1a9ad-120">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="1a9ad-121">Yüklenen CLRs numaralandırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-121">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a9ad-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a9ad-122">Remarks</span></span>  

 <span data-ttu-id="1a9ad-123">Tarafından tanımlanan bir hedef işlem için işlev, `debuggeePID` `ppStringArrayOut` işlem Içinde yüklenen CLRs 'ye bir yol dizisi döndürür; bu, `ppHandleArrayOut` clr için aynı dizinde devam eden bir başlatma olayı içerebilen olay tanıtıcısı dizisi ve `pdwArrayLengthOut` yüklenen CLRs sayısını belirten dizilerin boyutu.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-123">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="1a9ad-124">Windows işletim sisteminde `debuggeePID` BIR işletim sistemi işlem tanımlayıcısına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-124">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="1a9ad-125">Ve için bellek `ppHandleArrayOut` `ppStringArrayOut` Bu işlev tarafından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-125">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="1a9ad-126">Ayrılan belleği serbest bırakmak için [CloseCLREnumeration işlevini](closeclrenumeration-function.md)çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-126">To free the memory allocated, you must call [CloseCLREnumeration Function](closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="1a9ad-127">Bu işlev, hedef işlemdeki CLRs sayısını döndürmek için her iki dizi parametresi null olarak ayarlanmış şekilde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="1a9ad-127">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="1a9ad-128">Bu saydan bir arayan, oluşturulacak arabelleğin boyutunu çıkarabilir: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)` .</span><span class="sxs-lookup"><span data-stu-id="1a9ad-128">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a9ad-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a9ad-129">Requirements</span></span>  

 <span data-ttu-id="1a9ad-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a9ad-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a9ad-131">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="1a9ad-131">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="1a9ad-132">**Kitaplık:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="1a9ad-132">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="1a9ad-133">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="1a9ad-133">**.NET Framework Versions:** 3.5 SP1</span></span>
