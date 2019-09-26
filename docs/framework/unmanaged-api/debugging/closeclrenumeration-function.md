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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a05a779d4a56eb8f881da1824d5ffaa363b5a01
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274276"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="0a780-102">CloseCLREnumeration İşlevi</span><span class="sxs-lookup"><span data-stu-id="0a780-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="0a780-103">Geçerli ortak dil çalışma zamanı (CLR) Continue-, [EnumerateCLRs işlevi](enumerateclrs-function.md)tarafından döndürülen bir dizi tanıtıcıda bulunan Başlangıç olaylarını kapatır ve tanıtıcı ve dize yolu dizileri için belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="0a780-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a780-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a780-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a780-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a780-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="0a780-106">'ndaki [EnumerateCLRs işlevinden](enumerateclrs-function.md)döndürülen olay tanıtıcısı dizisine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0a780-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="0a780-107">'ndaki [EnumerateCLRs işlevinden](enumerateclrs-function.md)döndürülen CLR dize yollarının dizisine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0a780-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="0a780-108">'ndaki `pHandleArray` Ya`pStringArray` da (uzunluk) boyutunu (aynı) içeren DWORD.</span><span class="sxs-lookup"><span data-stu-id="0a780-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a780-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0a780-109">Return Value</span></span>  
 <span data-ttu-id="0a780-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a780-110">S_OK</span></span>  
 <span data-ttu-id="0a780-111">[EnumerateCLRs işlevi](enumerateclrs-function.md) tarafından açılan tutamaçlar kapatılır ve tanıtıcı ve dize dizileri için ayrılan bellek serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="0a780-111">Handles opened by the [EnumerateCLRs function](enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="0a780-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0a780-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="0a780-113">`pHandleArray` Uzunluğu`dwArrayLength`geçilen uzunlukla eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="0a780-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="0a780-114">E_FAıL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="0a780-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="0a780-115">İşlevi ve `pHandleArray` `pStringArray`için belleği serbest bırakılamıyor.</span><span class="sxs-lookup"><span data-stu-id="0a780-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a780-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a780-116">Requirements</span></span>  
 <span data-ttu-id="0a780-117">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a780-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a780-118">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="0a780-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="0a780-119">**Kitaplık:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="0a780-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="0a780-120">**.NET Framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="0a780-120">**.NET Framework Versions:** 3.5 SP1</span></span>
