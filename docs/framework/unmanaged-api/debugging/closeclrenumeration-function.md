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
ms.openlocfilehash: 1d42292705dae03e9bf1a1555508dfb69cebde82
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132429"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="7b128-102">CloseCLREnumeration İşlevi</span><span class="sxs-lookup"><span data-stu-id="7b128-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="7b128-103">Geçerli ortak dil çalışma zamanı (CLR) Continue-, [EnumerateCLRs işlevi](enumerateclrs-function.md)tarafından döndürülen bir dizi tanıtıcıda bulunan Başlangıç olaylarını kapatır ve tanıtıcı ve dize yolu dizileri için belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="7b128-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b128-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b128-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b128-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b128-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="7b128-106">'ndaki [EnumerateCLRs işlevinden](enumerateclrs-function.md)döndürülen olay tanıtıcısı dizisine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b128-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="7b128-107">'ndaki [EnumerateCLRs işlevinden](enumerateclrs-function.md)döndürülen CLR dize yollarının dizisine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b128-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="7b128-108">'ndaki `pHandleArray` ya da `pStringArray` boyutunu (uzunluk) içeren DWORD (aynı).</span><span class="sxs-lookup"><span data-stu-id="7b128-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b128-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7b128-109">Return Value</span></span>  
 <span data-ttu-id="7b128-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b128-110">S_OK</span></span>  
 <span data-ttu-id="7b128-111">[EnumerateCLRs işlevi](enumerateclrs-function.md) tarafından açılan tutamaçlar kapatılır ve tanıtıcı ve dize dizileri için ayrılan bellek serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="7b128-111">Handles opened by the [EnumerateCLRs function](enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="7b128-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7b128-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="7b128-113">`pHandleArray` uzunluğu `dwArrayLength`geçirilen uzunluğa uymuyor.</span><span class="sxs-lookup"><span data-stu-id="7b128-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="7b128-114">E_FAıL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="7b128-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7b128-115">İşlev, `pHandleArray` ve `pStringArray`için belleği serbest gönderemedi.</span><span class="sxs-lookup"><span data-stu-id="7b128-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b128-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b128-116">Requirements</span></span>  
 <span data-ttu-id="7b128-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b128-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b128-118">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="7b128-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="7b128-119">**Kitaplık:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="7b128-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="7b128-120">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="7b128-120">**.NET Framework Versions:** 3.5 SP1</span></span>
