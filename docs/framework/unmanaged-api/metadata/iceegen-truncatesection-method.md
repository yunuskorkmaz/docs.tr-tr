---
description: 'Şu konuda daha fazla bilgi edinin: ICeeGen:: TruncateSection Yöntemi'
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
ms.openlocfilehash: 074c7d7b4222b5b22f1d9b79169d531cd5544b1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784216"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="96b28-103">ICeeGen::TruncateSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96b28-103">ICeeGen::TruncateSection Method</span></span>

<span data-ttu-id="96b28-104">Belirtilen uzunluğa göre belirtilen kod bölümünü keser.</span><span class="sxs-lookup"><span data-stu-id="96b28-104">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="96b28-105">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="96b28-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b28-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96b28-106">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96b28-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96b28-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="96b28-108">'ndaki Kesmeyin bölüm.</span><span class="sxs-lookup"><span data-stu-id="96b28-108">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="96b28-109">'ndaki Bölümün kesirli kısmını kesmek için bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="96b28-109">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96b28-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96b28-110">Remarks</span></span>  

 <span data-ttu-id="96b28-111">`TruncateSection`Yalnızca diğer yöntemler tarafından işlenmemiş özel bölüm gereksinimleriniz varsa çağırın.</span><span class="sxs-lookup"><span data-stu-id="96b28-111">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96b28-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96b28-112">Requirements</span></span>  

 <span data-ttu-id="96b28-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96b28-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96b28-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="96b28-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96b28-115">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="96b28-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96b28-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96b28-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b28-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96b28-117">See also</span></span>

- [<span data-ttu-id="96b28-118">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96b28-118">ICeeGen Interface</span></span>](iceegen-interface.md)
