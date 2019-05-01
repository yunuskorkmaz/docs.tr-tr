---
title: IMetaDataEmit::DeleteFieldMarshal Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78f2405bba9172b775b01e5417860c3f3d2dd4a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992530"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="f236c-102">IMetaDataEmit::DeleteFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f236c-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="f236c-103">Belirtilen belirteç tarafından başvurulan nesne için meta verileri imza hazırlama PInvoke yok eder.</span><span class="sxs-lookup"><span data-stu-id="f236c-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f236c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f236c-104">Syntax</span></span>  
  
```  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f236c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f236c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f236c-106">[in] Bir `mdFieldDef` veya `mdParamDef` alanı veya sıralama meta verileri imza silmek istediğiniz parametreyi temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="f236c-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f236c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f236c-107">Requirements</span></span>  
 <span data-ttu-id="f236c-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f236c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f236c-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f236c-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f236c-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="f236c-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f236c-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f236c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f236c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f236c-112">See also</span></span>

- [<span data-ttu-id="f236c-113">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f236c-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f236c-114">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f236c-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
