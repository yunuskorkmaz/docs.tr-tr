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
ms.openlocfilehash: ed534890fc90d3b8543a1166c85903f10163f0a8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008343"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="c16d1-102">ICeeGen::GetSectionBlock Metodu</span><span class="sxs-lookup"><span data-stu-id="c16d1-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="c16d1-103">Kod tabanının bir bölüm bloğunu alır.</span><span class="sxs-lookup"><span data-stu-id="c16d1-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="c16d1-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c16d1-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c16d1-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c16d1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="c16d1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c16d1-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="c16d1-107">'ndaki Kod tabanı bloğunun alınacağı bölüm.</span><span class="sxs-lookup"><span data-stu-id="c16d1-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="c16d1-108">'ndaki Alınacak bloğun uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="c16d1-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="c16d1-109">'ndaki Bloğunun ilk baytını hizalamak için, bölümünün başlangıcına göre bayt.</span><span class="sxs-lookup"><span data-stu-id="c16d1-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="c16d1-110">Bu, bloğunun bölüm içindeki konumudur.</span><span class="sxs-lookup"><span data-stu-id="c16d1-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="c16d1-111">dışı Alınan bloğun adresini alan konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c16d1-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c16d1-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c16d1-112">Remarks</span></span>  
 <span data-ttu-id="c16d1-113">`GetSectionBlock`Yalnızca diğer yöntemler tarafından işlenmemiş özel bölüm gereksinimleriniz varsa çağırın.</span><span class="sxs-lookup"><span data-stu-id="c16d1-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c16d1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c16d1-114">Requirements</span></span>  
 <span data-ttu-id="c16d1-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c16d1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c16d1-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c16d1-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c16d1-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c16d1-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c16d1-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c16d1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c16d1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c16d1-119">See also</span></span>

- [<span data-ttu-id="c16d1-120">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c16d1-120">ICeeGen Interface</span></span>](iceegen-interface.md)
