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
ms.openlocfilehash: 8fe0df3ee08f9915ed43990b6f9686e25b183a0b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676107"
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="9cdab-102">EnumerateCLRs İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cdab-102">EnumerateCLRs Function</span></span>

<span data-ttu-id="9cdab-103">Bir işlemdeki CLRs 'yi listelemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cdab-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cdab-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9cdab-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cdab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9cdab-105">Parameters</span></span>  

 `debuggeePID`  
 <span data-ttu-id="9cdab-106">'ndaki Yüklenen CLRs 'nin numaralandıralınacağı işlemin işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9cdab-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="9cdab-107">dışı CLR başlatmaya devam etmek için kullanılan olay tutamaçlarını içeren bir diziye yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9cdab-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="9cdab-108">Dizideki her tanıtıcının geçerli olması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="9cdab-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="9cdab-109">Geçerliyse, tanıtıcı aynı dizininde bulunan ilgili çalışma zamanı için devam-başlatma olayı olarak kullanılır `ppStringArrayOut` .</span><span class="sxs-lookup"><span data-stu-id="9cdab-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="9cdab-110">dışı İşlemde yüklü olan tüm CLRs yollarını belirten dizeler dizisine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9cdab-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="9cdab-111">dışı Eşit büyüklükte boyut ve uzunluğu içeren bir DWORD işaretçisi `ppHandleArrayOut` `pdwArrayLengthOut` .</span><span class="sxs-lookup"><span data-stu-id="9cdab-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cdab-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9cdab-112">Return Value</span></span>  

 <span data-ttu-id="9cdab-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9cdab-113">S_OK</span></span>  
 <span data-ttu-id="9cdab-114">İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.</span><span class="sxs-lookup"><span data-stu-id="9cdab-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="9cdab-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9cdab-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="9cdab-116">Ya da null ya da `ppHandleArrayOut` `ppStringArrayOut` `pdwArrayLengthOut` null.</span><span class="sxs-lookup"><span data-stu-id="9cdab-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="9cdab-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9cdab-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="9cdab-118">İşlev, tanıtıcı ve yol dizileri için yeterli bellek ayıramadı.</span><span class="sxs-lookup"><span data-stu-id="9cdab-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="9cdab-119">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="9cdab-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="9cdab-120">Yüklenen CLRs numaralandırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="9cdab-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cdab-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9cdab-121">Remarks</span></span>  

 <span data-ttu-id="9cdab-122">Tarafından tanımlanan bir hedef işlem için işlev, `debuggeePID` `ppStringArrayOut` işlem Içinde yüklenen CLRs 'ye bir yol dizisi döndürür; bu, `ppHandleArrayOut` clr için aynı dizinde devam eden bir başlatma olayı içerebilen olay tanıtıcısı dizisi ve `pdwArrayLengthOut` yüklenen CLRs sayısını belirten dizilerin boyutu.</span><span class="sxs-lookup"><span data-stu-id="9cdab-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="9cdab-123">Windows işletim sisteminde `debuggeePID` BIR işletim sistemi işlem tanımlayıcısına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="9cdab-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="9cdab-124">Ve için bellek `ppHandleArrayOut` `ppStringArrayOut` Bu işlev tarafından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="9cdab-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="9cdab-125">Ayrılan belleği serbest bırakmak için [CloseCLREnumeration işlevini](closeclrenumeration-function.md)çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9cdab-125">To free the memory allocated, you must call [CloseCLREnumeration Function](closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="9cdab-126">Bu işlev, hedef işlemdeki CLRs sayısını döndürmek için her iki dizi parametresi null olarak ayarlanmış şekilde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="9cdab-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="9cdab-127">Bu saydan bir arayan, oluşturulacak arabelleğin boyutunu çıkarabilir: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)` .</span><span class="sxs-lookup"><span data-stu-id="9cdab-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cdab-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9cdab-128">Requirements</span></span>  

 <span data-ttu-id="9cdab-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cdab-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cdab-130">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="9cdab-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="9cdab-131">**Kitaplık:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="9cdab-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="9cdab-132">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="9cdab-132">**.NET Framework Versions:** 3.5 SP1</span></span>
