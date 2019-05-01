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
ms.openlocfilehash: 7e600f29a9036bb28031bd7854bc8cbb34c4566a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905508"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="6b22f-102">ICeeGen::GetSectionBlock Metodu</span><span class="sxs-lookup"><span data-stu-id="6b22f-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="6b22f-103">Kod tabanının bir bölüm bloğunu alır.</span><span class="sxs-lookup"><span data-stu-id="6b22f-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="6b22f-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b22f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b22f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b22f-105">Syntax</span></span>  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="6b22f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b22f-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="6b22f-107">[in] Bir blok kod tabanının alınacağı bölümü.</span><span class="sxs-lookup"><span data-stu-id="6b22f-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="6b22f-108">[in] Alınacak Blok uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="6b22f-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="6b22f-109">[in] Bloğun ilk baytı hizalamak hangi bölümde başlangıcına göre bayt.</span><span class="sxs-lookup"><span data-stu-id="6b22f-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="6b22f-110">Blok bölüm içindeki konumudur.</span><span class="sxs-lookup"><span data-stu-id="6b22f-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="6b22f-111">[out] Alınan blok adresini alan bir konuma yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6b22f-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b22f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b22f-112">Remarks</span></span>  
 <span data-ttu-id="6b22f-113">Çağrı `GetSectionBlock` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleriniz varsa.</span><span class="sxs-lookup"><span data-stu-id="6b22f-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b22f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b22f-114">Requirements</span></span>  
 <span data-ttu-id="6b22f-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b22f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b22f-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6b22f-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b22f-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="6b22f-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b22f-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b22f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b22f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b22f-119">See also</span></span>

- [<span data-ttu-id="6b22f-120">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b22f-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
