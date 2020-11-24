---
title: CloseCLREnumeration İşlevi
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
ms.openlocfilehash: 575e194cf952f02a3fe4fce9e955e45e1bc3653d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673919"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="b2e7c-102">CloseCLREnumeration İşlevi</span><span class="sxs-lookup"><span data-stu-id="b2e7c-102">CloseCLREnumeration Function</span></span>

<span data-ttu-id="b2e7c-103">Geçerli ortak dil çalışma zamanı (CLR) Continue-, [EnumerateCLRs işlevi](enumerateclrs-function.md)tarafından döndürülen bir dizi tanıtıcıda bulunan Başlangıç olaylarını kapatır ve tanıtıcı ve dize yolu dizileri için belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="b2e7c-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2e7c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b2e7c-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2e7c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2e7c-105">Parameters</span></span>  

 `pHandleArray`  
 <span data-ttu-id="b2e7c-106">'ndaki [EnumerateCLRs işlevinden](enumerateclrs-function.md)döndürülen olay tanıtıcısı dizisine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b2e7c-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="b2e7c-107">'ndaki [EnumerateCLRs işlevinden](enumerateclrs-function.md)döndürülen CLR dize yollarının dizisine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b2e7c-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="b2e7c-108">'ndaki Ya da (uzunluk) boyutunu ( `pHandleArray` aynı) IÇEREN DWORD `pStringArray` .</span><span class="sxs-lookup"><span data-stu-id="b2e7c-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2e7c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b2e7c-109">Return Value</span></span>  

 <span data-ttu-id="b2e7c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2e7c-110">S_OK</span></span>  
 <span data-ttu-id="b2e7c-111">[EnumerateCLRs işlevi](enumerateclrs-function.md) tarafından açılan tutamaçlar kapatılır ve tanıtıcı ve dize dizileri için ayrılan bellek serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="b2e7c-111">Handles opened by the [EnumerateCLRs function](enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="b2e7c-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b2e7c-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="b2e7c-113">Uzunluğu `pHandleArray` geçilen uzunlukla eşleşmiyor `dwArrayLength` .</span><span class="sxs-lookup"><span data-stu-id="b2e7c-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="b2e7c-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="b2e7c-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b2e7c-115">İşlevi ve için belleği serbest bırakılamıyor `pHandleArray` `pStringArray` .</span><span class="sxs-lookup"><span data-stu-id="b2e7c-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2e7c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2e7c-116">Requirements</span></span>  

 <span data-ttu-id="b2e7c-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2e7c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2e7c-118">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="b2e7c-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="b2e7c-119">**Kitaplık:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="b2e7c-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="b2e7c-120">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="b2e7c-120">**.NET Framework Versions:** 3.5 SP1</span></span>
