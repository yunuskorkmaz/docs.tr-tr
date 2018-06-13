---
title: ICeeGen::GetSectionBlock Metodu
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5da2936a46dcf3d8f69acc3367db64712165b0cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444076"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="22bc2-102">ICeeGen::GetSectionBlock Metodu</span><span class="sxs-lookup"><span data-stu-id="22bc2-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="22bc2-103">Kod temeliniz bölüm bloğunu alır.</span><span class="sxs-lookup"><span data-stu-id="22bc2-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="22bc2-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="22bc2-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22bc2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22bc2-105">Syntax</span></span>  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="22bc2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22bc2-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="22bc2-107">[in] Kod temeliniz bloğunu alınacağı bölümü.</span><span class="sxs-lookup"><span data-stu-id="22bc2-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="22bc2-108">[in] Alınacak Blok uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="22bc2-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="22bc2-109">[in] Hangi blok ilk baytını hizalamak bölüm başına göreli bayt.</span><span class="sxs-lookup"><span data-stu-id="22bc2-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="22bc2-110">Blok bölüm içindeki konumudur.</span><span class="sxs-lookup"><span data-stu-id="22bc2-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="22bc2-111">[out] Bir işaretçi bir konuma alınan blok adresi alır.</span><span class="sxs-lookup"><span data-stu-id="22bc2-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22bc2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22bc2-112">Remarks</span></span>  
 <span data-ttu-id="22bc2-113">Çağrı `GetSectionBlock` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleri varsa.</span><span class="sxs-lookup"><span data-stu-id="22bc2-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22bc2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22bc2-114">Requirements</span></span>  
 <span data-ttu-id="22bc2-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22bc2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22bc2-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="22bc2-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22bc2-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="22bc2-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22bc2-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22bc2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22bc2-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22bc2-119">See Also</span></span>  
 [<span data-ttu-id="22bc2-120">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22bc2-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
