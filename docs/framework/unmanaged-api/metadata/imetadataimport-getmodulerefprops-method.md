---
title: IMetaDataImport::GetModuleRefProps Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e948644e4f2d91b2f1e3e3627f7adbe204dee9d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777682"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="8217f-102">IMetaDataImport::GetModuleRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8217f-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="8217f-103">Belirtilen meta veri belirteci tarafından başvurulan modül adını alır.</span><span class="sxs-lookup"><span data-stu-id="8217f-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8217f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8217f-104">Syntax</span></span>  
  
```  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8217f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8217f-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="8217f-106">[in] Meta veri bilgilerini almak için modülüne başvuruyor ModuleRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="8217f-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="8217f-107">[out] Modül adı tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="8217f-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8217f-108">[in] İstenen boyutu `szName` geniş karakter.</span><span class="sxs-lookup"><span data-stu-id="8217f-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8217f-109">[out] Döndürülen boyutunu `szName` geniş karakter.</span><span class="sxs-lookup"><span data-stu-id="8217f-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8217f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8217f-110">Requirements</span></span>  
 <span data-ttu-id="8217f-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8217f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8217f-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8217f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8217f-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8217f-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8217f-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8217f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8217f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8217f-115">See also</span></span>

- [<span data-ttu-id="8217f-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8217f-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8217f-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8217f-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
