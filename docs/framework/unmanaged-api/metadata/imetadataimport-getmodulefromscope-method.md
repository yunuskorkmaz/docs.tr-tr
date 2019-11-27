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
ms.openlocfilehash: 026a952e14cda2ef4ebc32ca91006026e920e3c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437365"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="d5470-102">IMetaDataImport::GetModuleFromScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5470-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="d5470-103">Geçerli meta veri kapsamında başvurulan modül için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="d5470-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5470-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5470-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5470-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5470-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="d5470-106">dışı Geçerli meta veri kapsamında başvurulan modülü temsil eden belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5470-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5470-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5470-107">Requirements</span></span>  
 <span data-ttu-id="d5470-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5470-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5470-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d5470-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5470-110">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d5470-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5470-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5470-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5470-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5470-112">See also</span></span>

- [<span data-ttu-id="d5470-113">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5470-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d5470-114">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5470-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
