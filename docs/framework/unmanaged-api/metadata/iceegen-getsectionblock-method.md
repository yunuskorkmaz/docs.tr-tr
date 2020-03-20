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
ms.openlocfilehash: a494b1aaa762549528e92ab93d18929ef73eb8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176090"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="0b69a-102">ICeeGen::GetSectionBlock Metodu</span><span class="sxs-lookup"><span data-stu-id="0b69a-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="0b69a-103">Kod tabanının bir bölüm bloğunu alır.</span><span class="sxs-lookup"><span data-stu-id="0b69a-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="0b69a-104">Bu yöntem eskidir ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b69a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b69a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b69a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="0b69a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b69a-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="0b69a-107">[içinde] Kod tabanının bir bloğunu almak için hangi bölüm.</span><span class="sxs-lookup"><span data-stu-id="0b69a-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="0b69a-108">[içinde] Alınacak bloğun uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="0b69a-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="0b69a-109">[içinde] Bloğun ilk baytını hizalamak için bölümün başına göre bayt.</span><span class="sxs-lookup"><span data-stu-id="0b69a-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="0b69a-110">Bu, bloğun bölüm içindeki konumudur.</span><span class="sxs-lookup"><span data-stu-id="0b69a-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="0b69a-111">[çıkış] Alınan bloğun adresini alan bir konuma işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0b69a-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b69a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b69a-112">Remarks</span></span>  
 <span data-ttu-id="0b69a-113">Yalnızca `GetSectionBlock` diğer yöntemlerle işlenmemiş özel bölüm gereksinimleriniz varsa arayın.</span><span class="sxs-lookup"><span data-stu-id="0b69a-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b69a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b69a-114">Requirements</span></span>  
 <span data-ttu-id="0b69a-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b69a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b69a-116">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0b69a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b69a-117">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0b69a-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b69a-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b69a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b69a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b69a-119">See also</span></span>

- [<span data-ttu-id="0b69a-120">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b69a-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
