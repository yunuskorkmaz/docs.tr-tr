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
ms.openlocfilehash: a9eb9bb1e4abeb98d8d0ba2b052612d918c45f22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741091"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="2bac2-102">CloseCLREnumeration İşlevi</span><span class="sxs-lookup"><span data-stu-id="2bac2-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="2bac2-103">Bir dizi tarafından döndürülen tanıtıcı bulunan geçerli ortak dil çalışma zamanı (CLR) devam başlangıç olaylara kapatır [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)ve tanıtıcı ve dize yolu diziler için belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="2bac2-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bac2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2bac2-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bac2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2bac2-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="2bac2-106">[in] Sağlayıcıdan döndürülen olay tanıtıcı dizisine işaretçisine [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="2bac2-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="2bac2-107">[in] CLR dize yolları öğesinden döndürülen bir dizi işaretçi [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="2bac2-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="2bac2-108">[in] Boyutu (uzunluk) ya da içeren DWORD `pHandleArray` veya `pStringArray` (bunlar aynıdır).</span><span class="sxs-lookup"><span data-stu-id="2bac2-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2bac2-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2bac2-109">Return Value</span></span>  
 <span data-ttu-id="2bac2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2bac2-110">S_OK</span></span>  
 <span data-ttu-id="2bac2-111">Tanıtıcıları açan [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) kapalı olduğundan ve tanıtıcı ve dize diziler için ayrılan belleği serbest.</span><span class="sxs-lookup"><span data-stu-id="2bac2-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="2bac2-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2bac2-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="2bac2-113">Uzunluğunu `pHandleArray` geçirilen uzunluğu eşleşmiyor `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="2bac2-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="2bac2-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="2bac2-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="2bac2-115">İşlev için belleği serbest silemiyor `pHandleArray` ve `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="2bac2-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bac2-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2bac2-116">Requirements</span></span>  
 <span data-ttu-id="2bac2-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bac2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bac2-118">**Başlık:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="2bac2-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="2bac2-119">**Kitaplığı:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="2bac2-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="2bac2-120">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="2bac2-120">**.NET Framework Versions:** 3.5 SP1</span></span>
