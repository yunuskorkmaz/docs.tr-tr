---
title: IMetaDataImport::GetModuleRefProps Metodu
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
ms.openlocfilehash: e8d6549395c6c61f5f94a4b34ad0e3739737ed1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447051"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="b4ef0-102">IMetaDataImport::GetModuleRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="b4ef0-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="b4ef0-103">Belirtilen meta veri simgesi tarafından başvurulan modül adını alır.</span><span class="sxs-lookup"><span data-stu-id="b4ef0-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4ef0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4ef0-104">Syntax</span></span>  
  
```  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4ef0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4ef0-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="b4ef0-106">[in] Meta veri bilgilerini almak için modülüne başvuruyor ModuleRef meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="b4ef0-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="b4ef0-107">[out] Modül adı tutacak bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="b4ef0-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b4ef0-108">[in] İstenen boyutu `szName` geniş karakter.</span><span class="sxs-lookup"><span data-stu-id="b4ef0-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b4ef0-109">[out] Döndürülen boyutu `szName` geniş karakter.</span><span class="sxs-lookup"><span data-stu-id="b4ef0-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4ef0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4ef0-110">Requirements</span></span>  
 <span data-ttu-id="b4ef0-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4ef0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4ef0-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b4ef0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b4ef0-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b4ef0-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b4ef0-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4ef0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ef0-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b4ef0-115">See Also</span></span>  
 [<span data-ttu-id="b4ef0-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4ef0-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b4ef0-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4ef0-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
