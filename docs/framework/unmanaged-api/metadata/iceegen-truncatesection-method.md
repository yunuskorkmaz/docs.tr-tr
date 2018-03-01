---
title: "ICeeGen::TruncateSection Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e7deaaab58f1ee51bd3675faec892db5228c787
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="f047c-102">ICeeGen::TruncateSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f047c-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="f047c-103">Belirtilen kod bölümünde belirtilen uzunluğa göre keser.</span><span class="sxs-lookup"><span data-stu-id="f047c-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="f047c-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f047c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f047c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f047c-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f047c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f047c-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="f047c-107">[in] Truncate bölümü.</span><span class="sxs-lookup"><span data-stu-id="f047c-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="f047c-108">[in] Bölüm kesmek üzere bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f047c-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f047c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f047c-109">Remarks</span></span>  
 <span data-ttu-id="f047c-110">Çağrı `TruncateSection` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleri varsa.</span><span class="sxs-lookup"><span data-stu-id="f047c-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f047c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f047c-111">Requirements</span></span>  
 <span data-ttu-id="f047c-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f047c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f047c-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f047c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f047c-114">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f047c-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f047c-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f047c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f047c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f047c-116">See Also</span></span>  
 [<span data-ttu-id="f047c-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f047c-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
