---
title: IMetaDataImport::GetModuleRefProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetModuleRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 907743481cf036b7febf57d69ce428a250752c30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="c9108-102">IMetaDataImport::GetModuleRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="c9108-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="c9108-103">Belirtilen meta veri simgesi tarafından başvurulan modül adını alır.</span><span class="sxs-lookup"><span data-stu-id="c9108-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9108-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9108-104">Syntax</span></span>  
  
```  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9108-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9108-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="c9108-106">[in] Meta veri bilgilerini almak için modülüne başvuruyor ModuleRef meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="c9108-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="c9108-107">[out] Modül adı tutacak bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="c9108-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c9108-108">[in] İstenen boyutu `szName` geniş karakter.</span><span class="sxs-lookup"><span data-stu-id="c9108-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="c9108-109">[out] Döndürülen boyutu `szName` geniş karakter.</span><span class="sxs-lookup"><span data-stu-id="c9108-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9108-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9108-110">Requirements</span></span>  
 <span data-ttu-id="c9108-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9108-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9108-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c9108-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9108-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c9108-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9108-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9108-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9108-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9108-115">See Also</span></span>  
 [<span data-ttu-id="c9108-116">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9108-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c9108-117">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9108-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
