---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineSecurityAttributeSet yöntemi'
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
ms.openlocfilehash: 3512857ca23d65389b0e150bd24234d272ddd9b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784060"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="5d948-103">IMetaDataEmit::DefineSecurityAttributeSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d948-103">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>

<span data-ttu-id="5d948-104">Belirtilen belirteç tarafından başvurulan nesneye iliştirilecek bir güvenlik izinleri kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d948-104">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d948-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d948-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d948-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d948-106">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="5d948-107">'ndaki Güvenlik bilgilerinin eklendiği belirteç.</span><span class="sxs-lookup"><span data-stu-id="5d948-107">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="5d948-108">'ndaki `COR_SECATTR` Yapı dizisi.</span><span class="sxs-lookup"><span data-stu-id="5d948-108">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="5d948-109">'ndaki İçindeki öğe sayısı `rSecAttrs` .</span><span class="sxs-lookup"><span data-stu-id="5d948-109">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="5d948-110">dışı Yöntem başarısız olursa, `rSecAttrs` soruna neden olan öğenin içindeki dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d948-110">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d948-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d948-111">Requirements</span></span>  

 <span data-ttu-id="5d948-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d948-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d948-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5d948-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d948-114">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5d948-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d948-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d948-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d948-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d948-116">See also</span></span>

- [<span data-ttu-id="5d948-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d948-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5d948-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d948-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
