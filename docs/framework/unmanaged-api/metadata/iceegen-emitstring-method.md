---
title: "ICeeGen::EmitString Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 89c53f41595416a6bb4b8d373c7d3dbcea4c4faa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="bd361-102">ICeeGen::EmitString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd361-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="bd361-103">Belirtilen dize kod temeli yayar.</span><span class="sxs-lookup"><span data-stu-id="bd361-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="bd361-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bd361-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd361-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd361-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd361-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd361-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="bd361-107">[in] Yayma dize.</span><span class="sxs-lookup"><span data-stu-id="bd361-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="bd361-108">[out] Göreli sanal adres verilmiş dizesi.</span><span class="sxs-lookup"><span data-stu-id="bd361-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd361-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd361-109">Requirements</span></span>  
 <span data-ttu-id="bd361-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd361-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd361-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bd361-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd361-112">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="bd361-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd361-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd361-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd361-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd361-114">See Also</span></span>  
 [<span data-ttu-id="bd361-115">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd361-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
