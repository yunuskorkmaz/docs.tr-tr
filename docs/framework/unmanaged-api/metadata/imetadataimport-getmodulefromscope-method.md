---
title: IMetaDataImport::GetModuleFromScope Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 2eddd7a80c2b9c1b71f3e7fc5b1e4686ba11bccd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733171"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="bb73f-102">IMetaDataImport::GetModuleFromScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb73f-102">IMetaDataImport::GetModuleFromScope Method</span></span>

<span data-ttu-id="bb73f-103">Geçerli meta veri kapsamında başvurulan modül için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="bb73f-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb73f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bb73f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb73f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb73f-105">Parameters</span></span>  

 `pmd`  
 <span data-ttu-id="bb73f-106">dışı Geçerli meta veri kapsamında başvurulan modülü temsil eden belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bb73f-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb73f-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb73f-107">Requirements</span></span>  

 <span data-ttu-id="bb73f-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb73f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb73f-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bb73f-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb73f-110">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bb73f-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb73f-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb73f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb73f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb73f-112">See also</span></span>

- [<span data-ttu-id="bb73f-113">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb73f-113">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="bb73f-114">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb73f-114">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
