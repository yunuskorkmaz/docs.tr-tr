---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataImport:: IsGlobal yöntemi'
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
ms.openlocfilehash: 5230b2967990e3c52b429d62dd03566c3043e45f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789079"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="ee68a-103">IMetaDataImport::IsGlobal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee68a-103">IMetaDataImport::IsGlobal Method</span></span>

<span data-ttu-id="ee68a-104">Belirtilen meta veri belirteci tarafından temsil edilen alanın, yöntemin veya türün genel kapsama sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ee68a-104">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee68a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee68a-105">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee68a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee68a-106">Parameters</span></span>  

 `pd`  
 <span data-ttu-id="ee68a-107">'ndaki Bir türü, alanı veya yöntemi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="ee68a-107">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="ee68a-108">[out] nesnenin genel kapsamı varsa 1; Aksi takdirde, 0 (sıfır).</span><span class="sxs-lookup"><span data-stu-id="ee68a-108">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee68a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee68a-109">Requirements</span></span>  

 <span data-ttu-id="ee68a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee68a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee68a-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ee68a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee68a-112">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ee68a-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ee68a-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee68a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee68a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee68a-114">See also</span></span>

- [<span data-ttu-id="ee68a-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee68a-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ee68a-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee68a-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
