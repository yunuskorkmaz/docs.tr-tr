---
title: ICeeGen::GetSectionCreate Metodu
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
ms.openlocfilehash: 93e96e7804a3b5ecc64e9e50ce700435be83b77a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643370"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="3fdaa-102">ICeeGen::GetSectionCreate Metodu</span><span class="sxs-lookup"><span data-stu-id="3fdaa-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="3fdaa-103">Oluşturur ve belirtilen ada ve bayrak değerini kullanarak bir kod bölümü alır.</span><span class="sxs-lookup"><span data-stu-id="3fdaa-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="3fdaa-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3fdaa-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fdaa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fdaa-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fdaa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3fdaa-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="3fdaa-107">[in] Oluşturulacak bölümün adını belirten bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3fdaa-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="3fdaa-108">[in] Seçeneklerini belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="3fdaa-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="3fdaa-109">[out] Yeni oluşturulan kod bölümüne yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3fdaa-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fdaa-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fdaa-110">Remarks</span></span>  
 <span data-ttu-id="3fdaa-111">Çağrı `GetSectionCreate` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleriniz varsa.</span><span class="sxs-lookup"><span data-stu-id="3fdaa-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fdaa-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3fdaa-112">Requirements</span></span>  
 <span data-ttu-id="3fdaa-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fdaa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fdaa-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3fdaa-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fdaa-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="3fdaa-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fdaa-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fdaa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fdaa-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fdaa-117">See also</span></span>
- [<span data-ttu-id="3fdaa-118">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fdaa-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
