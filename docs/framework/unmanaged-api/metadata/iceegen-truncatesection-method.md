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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7b21179faec0b6f37b8084c9ee8a0bfd327193e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443570"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="8b556-102">ICeeGen::TruncateSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b556-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="8b556-103">Belirtilen kod bölümünde belirtilen uzunluğa göre keser.</span><span class="sxs-lookup"><span data-stu-id="8b556-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="8b556-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b556-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b556-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b556-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b556-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b556-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="8b556-107">[in] Truncate bölümü.</span><span class="sxs-lookup"><span data-stu-id="8b556-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="8b556-108">[in] Bölüm kesmek üzere bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="8b556-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b556-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b556-109">Remarks</span></span>  
 <span data-ttu-id="8b556-110">Çağrı `TruncateSection` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleri varsa.</span><span class="sxs-lookup"><span data-stu-id="8b556-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b556-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b556-111">Requirements</span></span>  
 <span data-ttu-id="8b556-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b556-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b556-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8b556-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b556-114">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8b556-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b556-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b556-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b556-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b556-116">See Also</span></span>  
 [<span data-ttu-id="8b556-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b556-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
