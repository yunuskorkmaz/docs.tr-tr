---
title: IMetaDataImport::GetScopeProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetScopeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b0936a9f47e2d0fa52816b78a7eecf3d244d594
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="cf75b-102">IMetaDataImport::GetScopeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="cf75b-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="cf75b-103">Ad ve isteğe bağlı olarak derleme veya modülü sürüm tanıtıcısı geçerli meta veri kapsamdaki alır.</span><span class="sxs-lookup"><span data-stu-id="cf75b-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf75b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf75b-104">Syntax</span></span>  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf75b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf75b-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="cf75b-106">[out] Bütünleştirilmiş kod veya modül adı için bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="cf75b-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="cf75b-107">[in] Geniş karakter cinsinden boyutu `szName`.</span><span class="sxs-lookup"><span data-stu-id="cf75b-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="cf75b-108">[out] Döndürülen geniş karakter sayısını `szName`.</span><span class="sxs-lookup"><span data-stu-id="cf75b-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="cf75b-109">[out, isteğe bağlı] Derleme veya Modül sürümü benzersiz olarak tanımlayan bir GUID için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cf75b-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf75b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf75b-110">Remarks</span></span>  
 <span data-ttu-id="cf75b-111">[Imetadataemit::setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) yöntemi bu özellikleri ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf75b-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf75b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf75b-112">Requirements</span></span>  
 <span data-ttu-id="cf75b-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf75b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf75b-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cf75b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf75b-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cf75b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf75b-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf75b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf75b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf75b-117">See Also</span></span>  
 [<span data-ttu-id="cf75b-118">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf75b-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cf75b-119">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf75b-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
