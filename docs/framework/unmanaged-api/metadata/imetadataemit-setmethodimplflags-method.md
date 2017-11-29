---
title: "IMetaDataEmit::SetMethodImplFlags Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetMethodImplFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d69940d5cffe397d009b7364a20a09dbbd95db4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="88299-102">IMetaDataEmit::SetMethodImplFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88299-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="88299-103">Belirtilen belirteç tarafından başvurulan devralınan yöntemi uygulama meta verileri imzası güncelleştirir veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="88299-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88299-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88299-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88299-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88299-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="88299-106">[in] Değiştirilecek yöntemi için belirteci.</span><span class="sxs-lookup"><span data-stu-id="88299-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="88299-107">[in] Değerleri bir birleşimini [Cormethodımpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) yöntemi uygulama özellikleri belirtir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="88299-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88299-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88299-108">Requirements</span></span>  
 <span data-ttu-id="88299-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88299-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88299-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="88299-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="88299-111">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="88299-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88299-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88299-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88299-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88299-113">See Also</span></span>  
 [<span data-ttu-id="88299-114">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="88299-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="88299-115">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="88299-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
