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
ms.openlocfilehash: b5015dc42497d269cdc2de944f14454558be6c07
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042751"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="7f3e7-102">IMetaDataImport::CountEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f3e7-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="7f3e7-103">Belirtilen numaralandırıcı tarafından alınan listedeki öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7f3e7-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f3e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f3e7-104">Syntax</span></span>  
  
```  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f3e7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f3e7-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="7f3e7-106">[in] Numaralandırıcı için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="7f3e7-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="7f3e7-107">[out] Numaralandırılan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="7f3e7-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f3e7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f3e7-108">Remarks</span></span>  
 <span data-ttu-id="7f3e7-109">Tarafından belirtilen işleç `hEnum` önceki bir sürümden elde edilen `Enum` *adı* arayın (örneğin, [Imetadataımport::enumtypedefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="7f3e7-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f3e7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f3e7-110">Requirements</span></span>  
 <span data-ttu-id="7f3e7-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f3e7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f3e7-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7f3e7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f3e7-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7f3e7-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f3e7-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f3e7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f3e7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f3e7-115">See also</span></span>

- [<span data-ttu-id="7f3e7-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f3e7-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7f3e7-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f3e7-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
