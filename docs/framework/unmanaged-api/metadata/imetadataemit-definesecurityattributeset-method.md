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
ms.openlocfilehash: fadd1974cd4fa8a51a06700835f46df24e37d7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175778"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="5ac5b-102">IMetaDataEmit::DefineSecurityAttributeSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ac5b-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="5ac5b-103">Belirtilen belirteç tarafından başvurulan nesneye eklemek için bir dizi güvenlik izni oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5ac5b-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ac5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ac5b-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ac5b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ac5b-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="5ac5b-106">[içinde] Güvenlik bilgilerinin bağlı olduğu belirteç.</span><span class="sxs-lookup"><span data-stu-id="5ac5b-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="5ac5b-107">[içinde] Bir dizi `COR_SECATTR` yapı.</span><span class="sxs-lookup"><span data-stu-id="5ac5b-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="5ac5b-108">[içinde] 'deki `rSecAttrs`öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="5ac5b-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="5ac5b-109">[çıkış] Yöntem başarısız olursa, soruna neden `rSecAttrs` olan öğenin dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ac5b-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ac5b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ac5b-110">Requirements</span></span>  
 <span data-ttu-id="5ac5b-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ac5b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ac5b-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5ac5b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ac5b-113">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5ac5b-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ac5b-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ac5b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac5b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ac5b-115">See also</span></span>

- [<span data-ttu-id="5ac5b-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ac5b-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5ac5b-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ac5b-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
