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
ms.openlocfilehash: d477976952d2c1875a620d1397fd43e5c5e2836f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503477"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="3f64b-102">IMetaDataImport::IsGlobal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f64b-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="3f64b-103">Belirtilen meta veri belirteci tarafından temsil edilen alanın, yöntemin veya türün genel kapsama sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="3f64b-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f64b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3f64b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f64b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f64b-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="3f64b-106">'ndaki Bir türü, alanı veya yöntemi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="3f64b-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="3f64b-107">[out] nesnenin genel kapsamı varsa 1; Aksi takdirde, 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="3f64b-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f64b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f64b-108">Requirements</span></span>  
 <span data-ttu-id="3f64b-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f64b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f64b-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3f64b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f64b-111">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3f64b-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f64b-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f64b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f64b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f64b-113">See also</span></span>

- [<span data-ttu-id="3f64b-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f64b-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3f64b-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f64b-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
