---
title: ICeeGen::AddSectionReloc Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: 129750644962cee3206b9e38cbeaa77d38dddd71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176116"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="19e06-102">ICeeGen::AddSectionReloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19e06-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="19e06-103">Kod tabanına bir .reloc yönergesi ekler.</span><span class="sxs-lookup"><span data-stu-id="19e06-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="19e06-104">Bu yöntem eskidir ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="19e06-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19e06-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19e06-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19e06-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19e06-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="19e06-107">[içinde] .reloc yönergesi ekleyeceğiniz bellek içi kod bölümü.</span><span class="sxs-lookup"><span data-stu-id="19e06-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="19e06-108">[içinde] Bölümün mahsup.</span><span class="sxs-lookup"><span data-stu-id="19e06-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="19e06-109">[içinde] Başvurulan `offset` bölüm.</span><span class="sxs-lookup"><span data-stu-id="19e06-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="19e06-110">[içinde] [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) değerlerinden biri, eklemek için .reloc yönergesi türünü gösteren.</span><span class="sxs-lookup"><span data-stu-id="19e06-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19e06-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19e06-111">Requirements</span></span>  
 <span data-ttu-id="19e06-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19e06-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19e06-113">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="19e06-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19e06-114">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="19e06-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="19e06-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19e06-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e06-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19e06-116">See also</span></span>

- [<span data-ttu-id="19e06-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19e06-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
