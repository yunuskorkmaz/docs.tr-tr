---
title: "ICeeGen::ComputePointer Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.ComputePointer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b027615f7697b9ea103d44bea0ec44834fe3f04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="a2c8e-102">ICeeGen::ComputePointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2c8e-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="a2c8e-103">Belirtilen kod bölümü için arabellek belirler.</span><span class="sxs-lookup"><span data-stu-id="a2c8e-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="a2c8e-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2c8e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c8e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2c8e-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2c8e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2c8e-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="a2c8e-107">[in] Kod bölümünde olan bir arabellek dönün.</span><span class="sxs-lookup"><span data-stu-id="a2c8e-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="a2c8e-108">[in] Bir işaretçi alma yöntemini göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="a2c8e-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="a2c8e-109">[out] Döndürülen arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a2c8e-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2c8e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2c8e-110">Requirements</span></span>  
 <span data-ttu-id="a2c8e-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2c8e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2c8e-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a2c8e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2c8e-113">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a2c8e-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2c8e-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2c8e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c8e-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2c8e-115">See Also</span></span>  
 [<span data-ttu-id="a2c8e-116">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2c8e-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
