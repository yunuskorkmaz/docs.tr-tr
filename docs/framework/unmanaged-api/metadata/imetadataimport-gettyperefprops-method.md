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
ms.openlocfilehash: a4d8829c9cb2818eafe98809c9a0d5fd8109d076
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778827"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="29d13-102">IMetaDataImport::GetTypeRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="29d13-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="29d13-103">İle ilişkili meta verileri alır <xref:System.Type> belirtilen TypeRef belirteci tarafından başvurulan.</span><span class="sxs-lookup"><span data-stu-id="29d13-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d13-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29d13-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29d13-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29d13-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="29d13-106">[in] Meta verileri için döndürülecek türünü temsil eden TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="29d13-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="29d13-107">[out] Başvuru yapıldığı kapsamı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="29d13-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="29d13-108">Bu değer bir AssemblyRef veya ModuleRef belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="29d13-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="29d13-109">[out] Tür adı içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="29d13-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="29d13-110">[in] Geniş karakter cinsinden istenen boyuta `szName`.</span><span class="sxs-lookup"><span data-stu-id="29d13-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="29d13-111">[out] Geniş karakter cinsinden döndürülen boyutu `szName`.</span><span class="sxs-lookup"><span data-stu-id="29d13-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d13-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29d13-112">Requirements</span></span>  
 <span data-ttu-id="29d13-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29d13-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29d13-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="29d13-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29d13-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="29d13-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29d13-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29d13-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d13-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29d13-117">See also</span></span>

- [<span data-ttu-id="29d13-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29d13-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="29d13-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29d13-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
