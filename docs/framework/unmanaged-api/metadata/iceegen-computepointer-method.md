---
title: ICeeGen::ComputePointer Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5fb63d4fe1e736ca1ff0c729d8d83cfe092eaaf5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465536"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="aea02-102">ICeeGen::ComputePointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aea02-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="aea02-103">Belirtilen kod bölümüne yönelik arabellek belirler.</span><span class="sxs-lookup"><span data-stu-id="aea02-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="aea02-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="aea02-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aea02-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aea02-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aea02-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aea02-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="aea02-107">[in] Kod bölümünde bir arabellek döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="aea02-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="aea02-108">[in] Yöntem bir işaretçi alınacağı göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="aea02-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="aea02-109">[out] Döndürülen arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aea02-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aea02-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aea02-110">Requirements</span></span>  
 <span data-ttu-id="aea02-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aea02-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aea02-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="aea02-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aea02-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="aea02-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aea02-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aea02-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea02-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aea02-115">See also</span></span>
- [<span data-ttu-id="aea02-116">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aea02-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
