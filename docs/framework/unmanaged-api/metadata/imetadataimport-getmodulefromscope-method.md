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
ms.openlocfilehash: 4e2b2501b6b7117cefcfa43511ef20f25106bb42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503594"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="14456-102">IMetaDataImport::GetModuleFromScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14456-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="14456-103">Geçerli meta veri kapsamında başvurulan modül için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="14456-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14456-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="14456-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14456-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14456-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="14456-106">dışı Geçerli meta veri kapsamında başvurulan modülü temsil eden belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="14456-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14456-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14456-107">Requirements</span></span>  
 <span data-ttu-id="14456-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14456-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14456-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="14456-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14456-110">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="14456-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="14456-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14456-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14456-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14456-112">See also</span></span>

- [<span data-ttu-id="14456-113">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14456-113">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="14456-114">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14456-114">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
