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
ms.openlocfilehash: 387f5f01f2d2589c0b34e50b69398e1feb0e77e0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008254"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="42455-102">ICeeGen::TruncateSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42455-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="42455-103">Belirtilen uzunluğa göre belirtilen kod bölümünü keser.</span><span class="sxs-lookup"><span data-stu-id="42455-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="42455-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="42455-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42455-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="42455-105">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42455-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="42455-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="42455-107">'ndaki Kesmeyin bölüm.</span><span class="sxs-lookup"><span data-stu-id="42455-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="42455-108">'ndaki Bölümün kesirli kısmını kesmek için bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="42455-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42455-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42455-109">Remarks</span></span>  
 <span data-ttu-id="42455-110">`TruncateSection`Yalnızca diğer yöntemler tarafından işlenmemiş özel bölüm gereksinimleriniz varsa çağırın.</span><span class="sxs-lookup"><span data-stu-id="42455-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42455-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42455-111">Requirements</span></span>  
 <span data-ttu-id="42455-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42455-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42455-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="42455-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42455-114">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="42455-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42455-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42455-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42455-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42455-116">See also</span></span>

- [<span data-ttu-id="42455-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="42455-117">ICeeGen Interface</span></span>](iceegen-interface.md)
