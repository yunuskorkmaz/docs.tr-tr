---
title: IMetaDataImport::CloseEnum Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7846eeceeb4d59c4e9aae73c79172c89184396e0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123875"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="67bd6-102">IMetaDataImport::CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67bd6-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="67bd6-103">Belirtilen tanıtıcı tarafından tanımlanan Numaralandırıcı kapatır.</span><span class="sxs-lookup"><span data-stu-id="67bd6-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67bd6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67bd6-104">Syntax</span></span>  
  
```  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67bd6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67bd6-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="67bd6-106">[in] Numaralandırıcının kapatmak için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="67bd6-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67bd6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67bd6-107">Remarks</span></span>  
 <span data-ttu-id="67bd6-108">Tarafından belirtilen işleç `hEnum` önceki bir sürümden elde edilen `Enum` *adı* arayın (örneğin, [Imetadataımport::enumtypedefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="67bd6-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67bd6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67bd6-109">Requirements</span></span>  
 <span data-ttu-id="67bd6-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67bd6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67bd6-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="67bd6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67bd6-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="67bd6-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="67bd6-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67bd6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67bd6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67bd6-114">See also</span></span>

- [<span data-ttu-id="67bd6-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67bd6-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="67bd6-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67bd6-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
