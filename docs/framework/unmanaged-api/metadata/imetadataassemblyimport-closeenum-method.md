---
title: "IMetaDataAssemblyImport::CloseEnum Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataAssemblyImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::CloseEnum
helpviewer_keywords:
- CloseEnum method, IMetaDataAssemblyImport interface [.NET Framework metadata]
- IMetaDataAssemblyImport::CloseEnum method [.NET Framework metadata]
ms.assetid: c9df4087-12b3-46d9-b075-9067dd7805df
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a0e015d59ff82c4baa3cefd4a32f393f518f291
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportcloseenum-method"></a><span data-ttu-id="6b23c-102">IMetaDataAssemblyImport::CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b23c-102">IMetaDataAssemblyImport::CloseEnum Method</span></span>
<span data-ttu-id="6b23c-103">Belirtilen numaralandırma örneğine başvuru serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="6b23c-103">Releases a reference to the specified enumeration instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b23c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b23c-104">Syntax</span></span>  
  
```  
void CloseEnum (  
    [in] HCORENUM     hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b23c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b23c-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="6b23c-106">[in] Kapatılması numaralandırması örneği.</span><span class="sxs-lookup"><span data-stu-id="6b23c-106">[in] The enumeration instance to be closed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b23c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b23c-107">Requirements</span></span>  
 <span data-ttu-id="6b23c-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b23c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b23c-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6b23c-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b23c-110">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6b23c-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b23c-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b23c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b23c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b23c-112">See Also</span></span>  
 [<span data-ttu-id="6b23c-113">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b23c-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
