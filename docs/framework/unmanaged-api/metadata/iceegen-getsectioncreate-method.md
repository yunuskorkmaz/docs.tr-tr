---
title: ICeeGen::GetSectionCreate Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03de69d51b520ae2d8be6c7f450f0541c52c36a2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472440"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="304c9-102">ICeeGen::GetSectionCreate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="304c9-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="304c9-103">Oluşturur ve belirtilen ada ve bayrak değerini kullanarak bir kod bölümü alır.</span><span class="sxs-lookup"><span data-stu-id="304c9-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="304c9-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="304c9-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="304c9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="304c9-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="304c9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="304c9-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="304c9-107">[in] Oluşturulacak bölümün adını belirten bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="304c9-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="304c9-108">[in] Seçeneklerini belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="304c9-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="304c9-109">[out] Yeni oluşturulan kod bölümüne yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="304c9-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="304c9-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="304c9-110">Remarks</span></span>  
 <span data-ttu-id="304c9-111">Çağrı `GetSectionCreate` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleriniz varsa.</span><span class="sxs-lookup"><span data-stu-id="304c9-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="304c9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="304c9-112">Requirements</span></span>  
 <span data-ttu-id="304c9-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="304c9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="304c9-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="304c9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="304c9-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="304c9-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="304c9-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="304c9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="304c9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="304c9-117">See also</span></span>
- [<span data-ttu-id="304c9-118">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="304c9-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
