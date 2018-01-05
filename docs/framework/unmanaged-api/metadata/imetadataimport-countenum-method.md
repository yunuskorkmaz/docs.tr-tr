---
title: "IMetaDataImport::CountEnum Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.CountEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26e826417e6fb48eb261278988bc7c351ee663aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="84c70-102">IMetaDataImport::CountEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84c70-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="84c70-103">Belirtilen numaralandırıcı tarafından alınan listedeki öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="84c70-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84c70-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84c70-104">Syntax</span></span>  
  
```  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84c70-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84c70-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="84c70-106">[in] Numaralandırıcı için işleci.</span><span class="sxs-lookup"><span data-stu-id="84c70-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="84c70-107">[out] Numaralandırılan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="84c70-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84c70-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84c70-108">Remarks</span></span>  
 <span data-ttu-id="84c70-109">Tarafından belirtilen tanıtıcı `hEnum` önceki bir sürümden alınır `Enum` *adı* çağrı (örneğin, [Imetadataımport::enumtypedefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="84c70-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84c70-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84c70-110">Requirements</span></span>  
 <span data-ttu-id="84c70-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84c70-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84c70-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="84c70-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="84c70-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="84c70-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="84c70-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84c70-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c70-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84c70-115">See Also</span></span>  
 [<span data-ttu-id="84c70-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84c70-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="84c70-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84c70-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
