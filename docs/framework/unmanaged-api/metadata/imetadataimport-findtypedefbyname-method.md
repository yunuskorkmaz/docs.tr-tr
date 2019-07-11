---
title: IMetaDataImport::FindTypeDefByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f182dad17e28cc5d19393bb4e13d747e34249fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782474"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="5b5d2-102">IMetaDataImport::FindTypeDefByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b5d2-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="5b5d2-103">TypeDef meta veriler için bir işaretçi için belirteç alır <xref:System.Type> belirtilen ada sahip.</span><span class="sxs-lookup"><span data-stu-id="5b5d2-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b5d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b5d2-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b5d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b5d2-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="5b5d2-106">[in] TypeDef belirteci almak üzere tür adı.</span><span class="sxs-lookup"><span data-stu-id="5b5d2-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="5b5d2-107">[in] Kapsayan sınıfı temsil eden bir tür tanımı veya TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="5b5d2-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="5b5d2-108">Bulunacak tür, iç içe geçmiş bir sınıf değil, bu değeri NULL olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5b5d2-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="5b5d2-109">[out] Eşleşen TypeDef belirteç için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5b5d2-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b5d2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b5d2-110">Requirements</span></span>  
 <span data-ttu-id="5b5d2-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b5d2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b5d2-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5b5d2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b5d2-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5b5d2-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5b5d2-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b5d2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b5d2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b5d2-115">See also</span></span>

- [<span data-ttu-id="5b5d2-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b5d2-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5b5d2-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b5d2-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
