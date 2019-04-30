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
ms.openlocfilehash: 808c48bb0c516c51f39a8424acf49869b1bc9208
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777491"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="c0af8-102">IMetaDataImport::GetTypeRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="c0af8-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="c0af8-103">İle ilişkili meta verileri alır <xref:System.Type> belirtilen TypeRef belirteci tarafından başvurulan.</span><span class="sxs-lookup"><span data-stu-id="c0af8-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0af8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0af8-104">Syntax</span></span>  
  
```  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0af8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0af8-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="c0af8-106">[in] Meta verileri için döndürülecek türünü temsil eden TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="c0af8-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="c0af8-107">[out] Başvuru yapıldığı kapsamı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c0af8-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="c0af8-108">Bu değer bir AssemblyRef veya ModuleRef belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="c0af8-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="c0af8-109">[out] Tür adı içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="c0af8-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c0af8-110">[in] Geniş karakter cinsinden istenen boyuta `szName`.</span><span class="sxs-lookup"><span data-stu-id="c0af8-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="c0af8-111">[out] Geniş karakter cinsinden döndürülen boyutu `szName`.</span><span class="sxs-lookup"><span data-stu-id="c0af8-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0af8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0af8-112">Requirements</span></span>  
 <span data-ttu-id="c0af8-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0af8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0af8-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c0af8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0af8-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c0af8-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0af8-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0af8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0af8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0af8-117">See also</span></span>

- [<span data-ttu-id="c0af8-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0af8-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c0af8-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0af8-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
