---
title: IMetaDataEmit::DefineSecurityAttributeSet Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineSecurityAttributeSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43009a81298fa5414df94e0664306859f0c9b851
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478753"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="94544-102">IMetaDataEmit::DefineSecurityAttributeSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94544-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="94544-103">Belirtilen belirteç tarafından başvurulan nesne iliştirmek için güvenlik izinleri kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="94544-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94544-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94544-104">Syntax</span></span>  
  
```  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94544-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94544-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="94544-106">[in] Güvenlik bilgilerini eklendiği belirteç.</span><span class="sxs-lookup"><span data-stu-id="94544-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="94544-107">[in] Bir dizi `COR_SECATTR` yapıları.</span><span class="sxs-lookup"><span data-stu-id="94544-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="94544-108">[in] İçindeki öğelerin sayısını `rSecAttrs`.</span><span class="sxs-lookup"><span data-stu-id="94544-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="94544-109">[out] Yöntem başarısız olursa, dizin belirtir `rSecAttrs` soruna neden olan öğe.</span><span class="sxs-lookup"><span data-stu-id="94544-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94544-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94544-110">Requirements</span></span>  
 <span data-ttu-id="94544-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94544-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94544-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="94544-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94544-113">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="94544-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94544-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94544-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94544-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94544-115">See also</span></span>
- [<span data-ttu-id="94544-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94544-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="94544-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94544-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
