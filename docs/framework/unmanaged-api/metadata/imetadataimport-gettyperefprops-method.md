---
title: IMetaDataImport::GetTypeRefProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 191a6e4fcfe340ed43e85a9aa90f8a2ec0931730
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671661"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="8a6ce-102">IMetaDataImport::GetTypeRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="8a6ce-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="8a6ce-103">İle ilişkili meta verileri alır <xref:System.Type> belirtilen TypeRef belirteci tarafından başvurulan.</span><span class="sxs-lookup"><span data-stu-id="8a6ce-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a6ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a6ce-104">Syntax</span></span>  
  
```  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a6ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a6ce-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="8a6ce-106">[in] Meta verileri için döndürülecek türünü temsil eden TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="8a6ce-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="8a6ce-107">[out] Başvuru yapıldığı kapsamı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8a6ce-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="8a6ce-108">Bu değer bir AssemblyRef veya ModuleRef belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="8a6ce-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a6ce-109">[out] Tür adı içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="8a6ce-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8a6ce-110">[in] Geniş karakter cinsinden istenen boyuta `szName`.</span><span class="sxs-lookup"><span data-stu-id="8a6ce-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8a6ce-111">[out] Geniş karakter cinsinden döndürülen boyutu `szName`.</span><span class="sxs-lookup"><span data-stu-id="8a6ce-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a6ce-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a6ce-112">Requirements</span></span>  
 <span data-ttu-id="8a6ce-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a6ce-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a6ce-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8a6ce-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a6ce-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8a6ce-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a6ce-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a6ce-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a6ce-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a6ce-117">See also</span></span>
- [<span data-ttu-id="8a6ce-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a6ce-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8a6ce-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a6ce-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
