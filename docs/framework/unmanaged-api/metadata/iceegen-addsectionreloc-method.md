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
ms.openlocfilehash: a8e270f45300bd5f8c2e6cd87f9b84f31ec42320
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722198"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="edf79-102">ICeeGen::AddSectionReloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="edf79-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="edf79-103">Kod tabanına .reloc yönergesi ekler.</span><span class="sxs-lookup"><span data-stu-id="edf79-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="edf79-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="edf79-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edf79-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edf79-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edf79-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="edf79-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="edf79-107">[in] Bellek içi kod .reloc yönerge eklenecek bölümünün.</span><span class="sxs-lookup"><span data-stu-id="edf79-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="edf79-108">[in] Bölümün uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="edf79-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="edf79-109">[in] Bölümüne `offset` ifade eder.</span><span class="sxs-lookup"><span data-stu-id="edf79-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="edf79-110">[in] Aşağıdakilerden birini [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) eklemek için .reloc yönerge türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="edf79-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edf79-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="edf79-111">Requirements</span></span>  
 <span data-ttu-id="edf79-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edf79-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edf79-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="edf79-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="edf79-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="edf79-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="edf79-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edf79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf79-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edf79-116">See also</span></span>
- [<span data-ttu-id="edf79-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="edf79-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
