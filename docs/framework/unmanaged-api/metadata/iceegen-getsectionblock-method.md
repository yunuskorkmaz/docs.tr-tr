---
description: 'Şu konuda daha fazla bilgi edinin: ICeeGen:: GetSectionBlock yöntemi'
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
ms.openlocfilehash: d1a9fdeb35507f9dd6528b581be877049d2a1478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721157"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="96db8-103">ICeeGen::GetSectionBlock Metodu</span><span class="sxs-lookup"><span data-stu-id="96db8-103">ICeeGen::GetSectionBlock Method</span></span>

<span data-ttu-id="96db8-104">Kod tabanının bir bölüm bloğunu alır.</span><span class="sxs-lookup"><span data-stu-id="96db8-104">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="96db8-105">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="96db8-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96db8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96db8-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="96db8-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96db8-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="96db8-108">'ndaki Kod tabanı bloğunun alınacağı bölüm.</span><span class="sxs-lookup"><span data-stu-id="96db8-108">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="96db8-109">'ndaki Alınacak bloğun uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="96db8-109">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="96db8-110">'ndaki Bloğunun ilk baytını hizalamak için, bölümünün başlangıcına göre bayt.</span><span class="sxs-lookup"><span data-stu-id="96db8-110">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="96db8-111">Bu, bloğunun bölüm içindeki konumudur.</span><span class="sxs-lookup"><span data-stu-id="96db8-111">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="96db8-112">dışı Alınan bloğun adresini alan konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="96db8-112">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96db8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96db8-113">Remarks</span></span>  

 <span data-ttu-id="96db8-114">`GetSectionBlock`Yalnızca diğer yöntemler tarafından işlenmemiş özel bölüm gereksinimleriniz varsa çağırın.</span><span class="sxs-lookup"><span data-stu-id="96db8-114">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96db8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96db8-115">Requirements</span></span>  

 <span data-ttu-id="96db8-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96db8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96db8-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="96db8-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96db8-118">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="96db8-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96db8-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96db8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96db8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96db8-120">See also</span></span>

- [<span data-ttu-id="96db8-121">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96db8-121">ICeeGen Interface</span></span>](iceegen-interface.md)
