---
title: IMetaDataImport::CountEnum Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b48ff81fad397adcd5b2d0caae961484bfea5e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706397"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="321bb-102">IMetaDataImport::CountEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="321bb-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="321bb-103">Belirtilen numaralandırıcı tarafından alınan listedeki öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="321bb-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="321bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="321bb-104">Syntax</span></span>  
  
```  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="321bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="321bb-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="321bb-106">[in] Numaralandırıcı için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="321bb-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="321bb-107">[out] Numaralandırılan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="321bb-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="321bb-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="321bb-108">Remarks</span></span>  
 <span data-ttu-id="321bb-109">Tarafından belirtilen işleç `hEnum` önceki bir sürümden elde edilen `Enum` *adı* arayın (örneğin, [Imetadataımport::enumtypedefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="321bb-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="321bb-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="321bb-110">Requirements</span></span>  
 <span data-ttu-id="321bb-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="321bb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="321bb-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="321bb-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="321bb-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="321bb-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="321bb-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="321bb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321bb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="321bb-115">See also</span></span>
- [<span data-ttu-id="321bb-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="321bb-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="321bb-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="321bb-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
