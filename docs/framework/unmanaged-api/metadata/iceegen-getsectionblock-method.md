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
ms.openlocfilehash: 9ce3afded5f914ecf970d8db738becc7f5cfff84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723148"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="2d0f2-102">ICeeGen::GetSectionBlock Metodu</span><span class="sxs-lookup"><span data-stu-id="2d0f2-102">ICeeGen::GetSectionBlock Method</span></span>

<span data-ttu-id="2d0f2-103">Kod tabanının bir bölüm bloğunu alır.</span><span class="sxs-lookup"><span data-stu-id="2d0f2-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="2d0f2-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d0f2-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d0f2-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2d0f2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="2d0f2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d0f2-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="2d0f2-107">'ndaki Kod tabanı bloğunun alınacağı bölüm.</span><span class="sxs-lookup"><span data-stu-id="2d0f2-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="2d0f2-108">'ndaki Alınacak bloğun uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="2d0f2-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="2d0f2-109">'ndaki Bloğunun ilk baytını hizalamak için, bölümünün başlangıcına göre bayt.</span><span class="sxs-lookup"><span data-stu-id="2d0f2-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="2d0f2-110">Bu, bloğunun bölüm içindeki konumudur.</span><span class="sxs-lookup"><span data-stu-id="2d0f2-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="2d0f2-111">dışı Alınan bloğun adresini alan konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2d0f2-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d0f2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d0f2-112">Remarks</span></span>  

 <span data-ttu-id="2d0f2-113">`GetSectionBlock`Yalnızca diğer yöntemler tarafından işlenmemiş özel bölüm gereksinimleriniz varsa çağırın.</span><span class="sxs-lookup"><span data-stu-id="2d0f2-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d0f2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d0f2-114">Requirements</span></span>  

 <span data-ttu-id="2d0f2-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d0f2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d0f2-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2d0f2-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d0f2-117">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2d0f2-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d0f2-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d0f2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d0f2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d0f2-119">See also</span></span>

- [<span data-ttu-id="2d0f2-120">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d0f2-120">ICeeGen Interface</span></span>](iceegen-interface.md)
