---
title: ICeeGen::GetSectionCreate Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionCreate
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2ea9cb20b62e1b1fa8e726ba0c49c5e24202530c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="3db40-102">ICeeGen::GetSectionCreate Metodu</span><span class="sxs-lookup"><span data-stu-id="3db40-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="3db40-103">Oluşturur ve belirtilen ad ve bayrak değerleri kullanarak bir kod bölümü alır.</span><span class="sxs-lookup"><span data-stu-id="3db40-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="3db40-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3db40-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3db40-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3db40-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3db40-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3db40-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="3db40-107">[in] Oluşturulacak bölümün adını belirten bir dize için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3db40-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="3db40-108">[in] Seçeneklerini belirtin bayraklar.</span><span class="sxs-lookup"><span data-stu-id="3db40-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="3db40-109">[out] Yeni oluşturulan kod bölümünde bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3db40-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3db40-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3db40-110">Remarks</span></span>  
 <span data-ttu-id="3db40-111">Çağrı `GetSectionCreate` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleri varsa.</span><span class="sxs-lookup"><span data-stu-id="3db40-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3db40-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3db40-112">Requirements</span></span>  
 <span data-ttu-id="3db40-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3db40-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3db40-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3db40-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3db40-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3db40-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3db40-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3db40-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db40-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3db40-117">See Also</span></span>  
 [<span data-ttu-id="3db40-118">Iceegen arabirimi</span><span class="sxs-lookup"><span data-stu-id="3db40-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
