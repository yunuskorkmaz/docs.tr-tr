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
ms.openlocfilehash: 1ef6583587b960d74c83350b061be3c2e36fd4f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722692"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="ad78c-102">ICeeGen::TruncateSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad78c-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="ad78c-103">Belirtilen kod bölümünde belirtilen uzunluğa göre keser.</span><span class="sxs-lookup"><span data-stu-id="ad78c-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="ad78c-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad78c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad78c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad78c-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad78c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad78c-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="ad78c-107">[in] Truncate bölümü.</span><span class="sxs-lookup"><span data-stu-id="ad78c-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="ad78c-108">[in] Bölüm kesmek, bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="ad78c-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad78c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad78c-109">Remarks</span></span>  
 <span data-ttu-id="ad78c-110">Çağrı `TruncateSection` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleriniz varsa.</span><span class="sxs-lookup"><span data-stu-id="ad78c-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad78c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad78c-111">Requirements</span></span>  
 <span data-ttu-id="ad78c-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad78c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad78c-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ad78c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad78c-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="ad78c-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad78c-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad78c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad78c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad78c-116">See also</span></span>
- [<span data-ttu-id="ad78c-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad78c-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
