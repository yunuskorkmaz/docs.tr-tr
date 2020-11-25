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
ms.openlocfilehash: 0d76abf8a9c923089f367ab4e1786ac8cc92622d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702985"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="6f98e-102">IMetaDataImport::IsGlobal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f98e-102">IMetaDataImport::IsGlobal Method</span></span>

<span data-ttu-id="6f98e-103">Belirtilen meta veri belirteci tarafından temsil edilen alanın, yöntemin veya türün genel kapsama sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="6f98e-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f98e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6f98e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f98e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f98e-105">Parameters</span></span>  

 `pd`  
 <span data-ttu-id="6f98e-106">'ndaki Bir türü, alanı veya yöntemi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="6f98e-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="6f98e-107">[out] nesnenin genel kapsamı varsa 1; Aksi takdirde, 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="6f98e-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f98e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f98e-108">Requirements</span></span>  

 <span data-ttu-id="6f98e-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f98e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f98e-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6f98e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f98e-111">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6f98e-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f98e-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f98e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f98e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f98e-113">See also</span></span>

- [<span data-ttu-id="6f98e-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f98e-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6f98e-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f98e-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
