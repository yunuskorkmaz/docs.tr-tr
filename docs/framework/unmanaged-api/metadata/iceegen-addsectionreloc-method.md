---
description: 'Şu konuda daha fazla bilgi edinin: ICeeGen:: AddSectionReloc yöntemi'
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
ms.openlocfilehash: 715c506f0bdcb3fcef33b3e9165d1f9ae47c6073
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707182"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="56389-103">ICeeGen::AddSectionReloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56389-103">ICeeGen::AddSectionReloc Method</span></span>

<span data-ttu-id="56389-104">Kod tabanına bir. reloc yönergesi ekler.</span><span class="sxs-lookup"><span data-stu-id="56389-104">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="56389-105">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="56389-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56389-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56389-106">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56389-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56389-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="56389-108">'ndaki . Reloc yönergesinin ekleneceği bellek içi kodun bölümü.</span><span class="sxs-lookup"><span data-stu-id="56389-108">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="56389-109">'ndaki Bölümün boşluğu.</span><span class="sxs-lookup"><span data-stu-id="56389-109">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="56389-110">'ndaki `offset` Başvurduğu bölüm.</span><span class="sxs-lookup"><span data-stu-id="56389-110">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="56389-111">'ndaki Add. reloc yönergesinin türünü gösteren [CeeSectionRelocType](ceesectionreloctype-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="56389-111">[in] One of the [CeeSectionRelocType](ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56389-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56389-112">Requirements</span></span>  

 <span data-ttu-id="56389-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56389-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56389-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="56389-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56389-115">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="56389-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56389-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56389-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56389-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56389-117">See also</span></span>

- [<span data-ttu-id="56389-118">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56389-118">ICeeGen Interface</span></span>](iceegen-interface.md)
