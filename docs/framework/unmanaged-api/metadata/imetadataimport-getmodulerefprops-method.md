---
title: IMetaDataImport::GetModuleRefProps Metodu
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
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ee230b691411c49ba4f0096d998ac229283fc02c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="2d71f-102">IMetaDataImport::GetModuleRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="2d71f-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="2d71f-103">Belirtilen meta veri simgesi tarafından başvurulan modül adını alır.</span><span class="sxs-lookup"><span data-stu-id="2d71f-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d71f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d71f-104">Syntax</span></span>  
  
```  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d71f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d71f-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="2d71f-106">[in] Meta veri bilgilerini almak için modülüne başvuruyor ModuleRef meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="2d71f-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="2d71f-107">[out] Modül adı tutacak bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="2d71f-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2d71f-108">[in] İstenen boyutu `szName` geniş karakter.</span><span class="sxs-lookup"><span data-stu-id="2d71f-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="2d71f-109">[out] Döndürülen boyutu `szName` geniş karakter.</span><span class="sxs-lookup"><span data-stu-id="2d71f-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d71f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d71f-110">Requirements</span></span>  
 <span data-ttu-id="2d71f-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d71f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d71f-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2d71f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d71f-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2d71f-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d71f-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d71f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d71f-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d71f-115">See Also</span></span>  
 [<span data-ttu-id="2d71f-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d71f-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="2d71f-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d71f-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
