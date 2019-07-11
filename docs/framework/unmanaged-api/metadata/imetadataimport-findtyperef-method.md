---
title: IMetaDataImport::FindTypeRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8159b5245598993a2075fb402b280f9ab4cb2cfa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782468"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="f92ee-102">IMetaDataImport::FindTypeRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f92ee-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="f92ee-103">Bir işaretçi için TypeRef belirteci alır <xref:System.Type> Belirtilen kapsam içinde olan ve belirtilen ada sahip bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="f92ee-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f92ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f92ee-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f92ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f92ee-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="f92ee-106">[in] Modül, derleme veya türünü belirten bir ModuleRef, AssemblyRef veya TypeRef belirteci sırasıyla, hangi tür başvurusu tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f92ee-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="f92ee-107">[in] Aramak için türü başvuru adı.</span><span class="sxs-lookup"><span data-stu-id="f92ee-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="f92ee-108">[out] Eşleşen TypeRef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f92ee-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f92ee-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f92ee-109">Requirements</span></span>  
 <span data-ttu-id="f92ee-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f92ee-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f92ee-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f92ee-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f92ee-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f92ee-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f92ee-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f92ee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f92ee-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f92ee-114">See also</span></span>

- [<span data-ttu-id="f92ee-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f92ee-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f92ee-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f92ee-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
