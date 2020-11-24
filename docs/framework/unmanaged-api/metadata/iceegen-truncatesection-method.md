---
title: ICeeGen::TruncateSection Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.TruncateSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type:
- apiref
ms.openlocfilehash: 3005db62bba4089c669a00f62e3c1e62f9e1dae9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685714"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="f1aff-102">ICeeGen::TruncateSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1aff-102">ICeeGen::TruncateSection Method</span></span>

<span data-ttu-id="f1aff-103">Belirtilen uzunluğa göre belirtilen kod bölümünü keser.</span><span class="sxs-lookup"><span data-stu-id="f1aff-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="f1aff-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1aff-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1aff-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f1aff-105">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1aff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1aff-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="f1aff-107">'ndaki Kesmeyin bölüm.</span><span class="sxs-lookup"><span data-stu-id="f1aff-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="f1aff-108">'ndaki Bölümün kesirli kısmını kesmek için bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f1aff-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1aff-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1aff-109">Remarks</span></span>  

 <span data-ttu-id="f1aff-110">`TruncateSection`Yalnızca diğer yöntemler tarafından işlenmemiş özel bölüm gereksinimleriniz varsa çağırın.</span><span class="sxs-lookup"><span data-stu-id="f1aff-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1aff-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1aff-111">Requirements</span></span>  

 <span data-ttu-id="f1aff-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1aff-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1aff-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f1aff-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1aff-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f1aff-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1aff-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1aff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1aff-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1aff-116">See also</span></span>

- [<span data-ttu-id="f1aff-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1aff-117">ICeeGen Interface</span></span>](iceegen-interface.md)
