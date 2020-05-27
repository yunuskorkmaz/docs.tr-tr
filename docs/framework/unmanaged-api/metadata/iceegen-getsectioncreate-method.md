---
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
ms.openlocfilehash: 0cf7b15392c90694db659f6faff6feecbef65466
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008345"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="d6696-102">ICeeGen::GetSectionCreate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6696-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="d6696-103">Belirtilen ad ve bayrak değerlerini kullanarak bir kod bölümü üretir ve alır.</span><span class="sxs-lookup"><span data-stu-id="d6696-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="d6696-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6696-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6696-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d6696-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6696-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6696-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d6696-107">'ndaki Oluşturulacak bölümün adını belirten bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d6696-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="d6696-108">'ndaki Seçenekleri belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="d6696-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="d6696-109">dışı Yeni oluşturulan kod bölümüne yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d6696-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6696-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6696-110">Remarks</span></span>  
 <span data-ttu-id="d6696-111">`GetSectionCreate`Yalnızca diğer yöntemler tarafından işlenmemiş özel bölüm gereksinimleriniz varsa çağırın.</span><span class="sxs-lookup"><span data-stu-id="d6696-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6696-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6696-112">Requirements</span></span>  
 <span data-ttu-id="d6696-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6696-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6696-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d6696-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6696-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d6696-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6696-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6696-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6696-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6696-117">See also</span></span>

- [<span data-ttu-id="d6696-118">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6696-118">ICeeGen Interface</span></span>](iceegen-interface.md)
