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
ms.openlocfilehash: 0731053fb37c775d25052a5fd99a479a44ff5862
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434873"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="30b73-102">ICeeGen::GetSectionBlock Metodu</span><span class="sxs-lookup"><span data-stu-id="30b73-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="30b73-103">Kod tabanının bir bölüm bloğunu alır.</span><span class="sxs-lookup"><span data-stu-id="30b73-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="30b73-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="30b73-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b73-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30b73-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="30b73-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30b73-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="30b73-107">'ndaki Kod tabanı bloğunun alınacağı bölüm.</span><span class="sxs-lookup"><span data-stu-id="30b73-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="30b73-108">'ndaki Alınacak bloğun uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="30b73-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="30b73-109">'ndaki Bloğunun ilk baytını hizalamak için, bölümünün başlangıcına göre bayt.</span><span class="sxs-lookup"><span data-stu-id="30b73-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="30b73-110">Bu, bloğunun bölüm içindeki konumudur.</span><span class="sxs-lookup"><span data-stu-id="30b73-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="30b73-111">dışı Alınan bloğun adresini alan konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="30b73-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30b73-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30b73-112">Remarks</span></span>  
 <span data-ttu-id="30b73-113">Yalnızca diğer yöntemler tarafından işlenmeyen özel bölüm gereksinimleriniz varsa `GetSectionBlock` çağırın.</span><span class="sxs-lookup"><span data-stu-id="30b73-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30b73-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30b73-114">Requirements</span></span>  
 <span data-ttu-id="30b73-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30b73-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30b73-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="30b73-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30b73-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="30b73-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30b73-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30b73-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b73-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30b73-119">See also</span></span>

- [<span data-ttu-id="30b73-120">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30b73-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
