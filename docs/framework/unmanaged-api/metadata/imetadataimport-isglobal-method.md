---
title: IMetaDataImport::IsGlobal Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4156c3507ccbd21d59893c5e03e15fe9b7322e48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447804"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="6f0ce-102">IMetaDataImport::IsGlobal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f0ce-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="6f0ce-103">Alan, yöntemi veya türü tarafından belirtilen meta veri simgesi gösterilir genel kapsama sahip olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="6f0ce-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f0ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f0ce-104">Syntax</span></span>  
  
```  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f0ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f0ce-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="6f0ce-106">[in] Türü, alan veya yöntem temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="6f0ce-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="6f0ce-107">[out] 1 IF nesne genel kapsama sahip; Aksi takdirde, 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="6f0ce-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f0ce-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f0ce-108">Requirements</span></span>  
 <span data-ttu-id="6f0ce-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f0ce-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f0ce-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6f0ce-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f0ce-111">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6f0ce-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f0ce-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f0ce-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f0ce-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f0ce-113">See Also</span></span>  
 [<span data-ttu-id="6f0ce-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f0ce-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="6f0ce-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f0ce-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
