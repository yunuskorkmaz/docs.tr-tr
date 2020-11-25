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
ms.openlocfilehash: 87a5224247c2d94613de482fbaa34bf978198bf0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715543"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="c1ffb-102">ICeeGen::AddSectionReloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ffb-102">ICeeGen::AddSectionReloc Method</span></span>

<span data-ttu-id="c1ffb-103">Kod tabanına bir. reloc yönergesi ekler.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="c1ffb-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ffb-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c1ffb-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1ffb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1ffb-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="c1ffb-107">'ndaki . Reloc yönergesinin ekleneceği bellek içi kodun bölümü.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="c1ffb-108">'ndaki Bölümün boşluğu.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="c1ffb-109">'ndaki `offset` Başvurduğu bölüm.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="c1ffb-110">'ndaki Add. reloc yönergesinin türünü gösteren [CeeSectionRelocType](ceesectionreloctype-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-110">[in] One of the [CeeSectionRelocType](ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1ffb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1ffb-111">Requirements</span></span>  

 <span data-ttu-id="c1ffb-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1ffb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1ffb-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c1ffb-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1ffb-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c1ffb-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1ffb-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1ffb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ffb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-116">See also</span></span>

- [<span data-ttu-id="c1ffb-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1ffb-117">ICeeGen Interface</span></span>](iceegen-interface.md)
