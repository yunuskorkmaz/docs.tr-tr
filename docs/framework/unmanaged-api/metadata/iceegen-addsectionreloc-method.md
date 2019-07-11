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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da3b83191ce1acdf40e27c5ee1d843a1fb4a54f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750682"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="89ec4-102">ICeeGen::AddSectionReloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89ec4-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="89ec4-103">Kod tabanına .reloc yönergesi ekler.</span><span class="sxs-lookup"><span data-stu-id="89ec4-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="89ec4-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="89ec4-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89ec4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89ec4-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89ec4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89ec4-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="89ec4-107">[in] Bellek içi kod .reloc yönerge eklenecek bölümünün.</span><span class="sxs-lookup"><span data-stu-id="89ec4-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="89ec4-108">[in] Bölümün uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="89ec4-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="89ec4-109">[in] Bölümüne `offset` ifade eder.</span><span class="sxs-lookup"><span data-stu-id="89ec4-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="89ec4-110">[in] Aşağıdakilerden birini [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) eklemek için .reloc yönerge türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="89ec4-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89ec4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89ec4-111">Requirements</span></span>  
 <span data-ttu-id="89ec4-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89ec4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89ec4-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="89ec4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89ec4-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="89ec4-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89ec4-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89ec4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ec4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89ec4-116">See also</span></span>

- [<span data-ttu-id="89ec4-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89ec4-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
