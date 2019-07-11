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
ms.openlocfilehash: 994f6668de3040cc9f2381356d6db06c18c9e984
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745886"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="514f7-102">ICeeGen::TruncateSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="514f7-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="514f7-103">Belirtilen kod bölümünde belirtilen uzunluğa göre keser.</span><span class="sxs-lookup"><span data-stu-id="514f7-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="514f7-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="514f7-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="514f7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="514f7-105">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="514f7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="514f7-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="514f7-107">[in] Truncate bölümü.</span><span class="sxs-lookup"><span data-stu-id="514f7-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="514f7-108">[in] Bölüm kesmek, bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="514f7-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="514f7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="514f7-109">Remarks</span></span>  
 <span data-ttu-id="514f7-110">Çağrı `TruncateSection` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleriniz varsa.</span><span class="sxs-lookup"><span data-stu-id="514f7-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="514f7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="514f7-111">Requirements</span></span>  
 <span data-ttu-id="514f7-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="514f7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="514f7-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="514f7-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="514f7-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="514f7-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="514f7-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="514f7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="514f7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="514f7-116">See also</span></span>

- [<span data-ttu-id="514f7-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="514f7-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
