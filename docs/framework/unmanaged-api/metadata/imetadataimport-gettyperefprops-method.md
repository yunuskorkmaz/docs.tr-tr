---
title: IMetaDataImport::GetTypeRefProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 55cb1d9eac13fc2d6d788eff039c4528e627ff12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="ccede-102">IMetaDataImport::GetTypeRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="ccede-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="ccede-103">İle ilişkili meta verileri alır <xref:System.Type> belirtilen TypeRef belirteç tarafından başvurulan.</span><span class="sxs-lookup"><span data-stu-id="ccede-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccede-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccede-104">Syntax</span></span>  
  
```  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccede-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ccede-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="ccede-106">[in] Meta veriler için dönüş türü temsil eder TypeRef simgesi.</span><span class="sxs-lookup"><span data-stu-id="ccede-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="ccede-107">[out] Başvuru yapıldığı kapsam için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ccede-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="ccede-108">Bu değer bir AssemblyRef veya ModuleRef belirteci olur.</span><span class="sxs-lookup"><span data-stu-id="ccede-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="ccede-109">[out] Tür adını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="ccede-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ccede-110">[in] Geniş karakterler istenen boyutta `szName`.</span><span class="sxs-lookup"><span data-stu-id="ccede-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="ccede-111">[out] Geniş karakterler döndürülen boyutu `szName`.</span><span class="sxs-lookup"><span data-stu-id="ccede-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccede-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ccede-112">Requirements</span></span>  
 <span data-ttu-id="ccede-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccede-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccede-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ccede-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ccede-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ccede-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ccede-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccede-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccede-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ccede-117">See Also</span></span>  
 [<span data-ttu-id="ccede-118">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="ccede-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ccede-119">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="ccede-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
