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
ms.openlocfilehash: c1f5f1c0ea5672812fca387b34238ada2a109938
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="0d2d2-102">ICeeGen::ComputePointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d2d2-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="0d2d2-103">Belirtilen kod bölümü için arabellek belirler.</span><span class="sxs-lookup"><span data-stu-id="0d2d2-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="0d2d2-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d2d2-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d2d2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d2d2-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d2d2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d2d2-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="0d2d2-107">[in] Kod bölümünde olan bir arabellek dönün.</span><span class="sxs-lookup"><span data-stu-id="0d2d2-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="0d2d2-108">[in] Bir işaretçi alma yöntemini göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="0d2d2-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="0d2d2-109">[out] Döndürülen arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0d2d2-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d2d2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d2d2-110">Requirements</span></span>  
 <span data-ttu-id="0d2d2-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d2d2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d2d2-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0d2d2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d2d2-113">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0d2d2-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d2d2-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d2d2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d2d2-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d2d2-115">See Also</span></span>  
 [<span data-ttu-id="0d2d2-116">Iceegen arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d2d2-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
