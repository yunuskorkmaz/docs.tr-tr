---
description: 'Şu konuda daha fazla bilgi edinin: ICeeGen:: GetSectionCreate yöntemi'
title: ICeeGen::GetSectionCreate Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
ms.openlocfilehash: 2839d11c927dbf573f213d3ebaa9e6e6d8d5015d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706870"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="6d149-103">ICeeGen::GetSectionCreate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d149-103">ICeeGen::GetSectionCreate Method</span></span>

<span data-ttu-id="6d149-104">Belirtilen ad ve bayrak değerlerini kullanarak bir kod bölümü üretir ve alır.</span><span class="sxs-lookup"><span data-stu-id="6d149-104">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="6d149-105">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6d149-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d149-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d149-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d149-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d149-107">Parameters</span></span>  

 `name`  
 <span data-ttu-id="6d149-108">'ndaki Oluşturulacak bölümün adını belirten bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6d149-108">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="6d149-109">'ndaki Seçenekleri belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="6d149-109">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="6d149-110">dışı Yeni oluşturulan kod bölümüne yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6d149-110">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d149-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d149-111">Remarks</span></span>  

 <span data-ttu-id="6d149-112">`GetSectionCreate`Yalnızca diğer yöntemler tarafından işlenmemiş özel bölüm gereksinimleriniz varsa çağırın.</span><span class="sxs-lookup"><span data-stu-id="6d149-112">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d149-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d149-113">Requirements</span></span>  

 <span data-ttu-id="6d149-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d149-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d149-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6d149-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d149-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6d149-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d149-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d149-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d149-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d149-118">See also</span></span>

- [<span data-ttu-id="6d149-119">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d149-119">ICeeGen Interface</span></span>](iceegen-interface.md)
