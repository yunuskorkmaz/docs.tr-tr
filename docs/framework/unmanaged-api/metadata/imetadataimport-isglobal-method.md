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
ms.openlocfilehash: 13f8a50f3fcbe9d6e7602ca3bbeb36587ecff32c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778792"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="17507-102">IMetaDataImport::IsGlobal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17507-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="17507-103">Alan, yöntem veya belirtilen metaveri belirteci tarafından temsil edilen tür genel kapsamda sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="17507-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17507-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17507-104">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17507-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17507-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="17507-106">[in] Tür, alan veya yöntemi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="17507-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="17507-107">[out] 1 ise, nesne genel kapsama sahip; Aksi takdirde, 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="17507-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17507-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17507-108">Requirements</span></span>  
 <span data-ttu-id="17507-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17507-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17507-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="17507-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17507-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="17507-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17507-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17507-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17507-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17507-113">See also</span></span>

- [<span data-ttu-id="17507-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17507-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="17507-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17507-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
