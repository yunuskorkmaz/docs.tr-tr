---
title: "CloseCLREnumeration İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CloseCLREnumeration
api_location: dbgshim.dll
api_type: COM
f1_keywords: CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f6de2d1625b4d9f66ec27ad7ed3e6ba33cc59b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="1be59-102">CloseCLREnumeration İşlevi</span><span class="sxs-lookup"><span data-stu-id="1be59-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="1be59-103">İşleyici tarafından döndürülen bir dizi bulunan geçerli ortak dil çalışma zamanı (CLR) devam başlangıç olaylara kapatır [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)ve tanıtıcısı ve dize yolu diziler için bellek boşaltır.</span><span class="sxs-lookup"><span data-stu-id="1be59-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1be59-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1be59-104">Syntax</span></span>  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1be59-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1be59-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="1be59-106">[in] Olay tanıtıcıları dizisi işaretçi döndürdü [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="1be59-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="1be59-107">[in] CLR dize yolları döndürülen dizi işaretçi [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="1be59-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="1be59-108">[in] Boyutunu (uzunluk) ya da içeren DWORD `pHandleArray` veya `pStringArray` (bunlar aynıdır).</span><span class="sxs-lookup"><span data-stu-id="1be59-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1be59-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1be59-109">Return Value</span></span>  
 <span data-ttu-id="1be59-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1be59-110">S_OK</span></span>  
 <span data-ttu-id="1be59-111">Tanıtıcıları açan [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) kapalı olduğundan ve işleyici ve dize diziler için ayrılan belleği serbest.</span><span class="sxs-lookup"><span data-stu-id="1be59-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="1be59-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1be59-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="1be59-113">Uzunluğu `pHandleArray` geçirilen uzunluğu eşleşmiyor `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="1be59-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="1be59-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="1be59-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="1be59-115">İşlev için belleği serbest alamıyor `pHandleArray` ve `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="1be59-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1be59-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1be59-116">Requirements</span></span>  
 <span data-ttu-id="1be59-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1be59-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1be59-118">**Başlık:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="1be59-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="1be59-119">**Kitaplığı:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="1be59-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="1be59-120">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="1be59-120">**.NET Framework Versions:** 3.5 SP1</span></span>
