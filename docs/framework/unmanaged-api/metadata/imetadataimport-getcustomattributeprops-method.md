---
title: IMetaDataImport::GetCustomAttributeProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetCustomAttributeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 415b1dc67bd3ae3638edd61558cc9e13ebf03fd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="26bb1-102">IMetaDataImport::GetCustomAttributeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="26bb1-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="26bb1-103">Meta veri simgesi verilen özel öznitelik değerini alır.</span><span class="sxs-lookup"><span data-stu-id="26bb1-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26bb1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26bb1-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26bb1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26bb1-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="26bb1-106">[in] Alınacak özel öznitelik temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="26bb1-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="26bb1-107">[out, isteğe bağlı] Özel öznitelik değiştirir nesnesini temsil eden bir meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="26bb1-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="26bb1-108">Bu değer, meta veri simgesi dışında herhangi bir türde olabilir `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="26bb1-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="26bb1-109">[out, isteğe bağlı] Bir `mdMethodDef` veya `mdMemberRef` meta verisini belirteci temsil eden <xref:System.Type> döndürülen özel özniteliğinin.</span><span class="sxs-lookup"><span data-stu-id="26bb1-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="26bb1-110">[out, isteğe bağlı] Bir özel öznitelik değeri veri dizisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="26bb1-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="26bb1-111">[out, isteğe bağlı] Döndürülen verileri bayt cinsinden boyutu *`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="26bb1-111">[out, optional] The size in bytes of the data returned in *`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26bb1-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26bb1-112">Remarks</span></span>  
 <span data-ttu-id="26bb1-113">Özel bir öznitelik, bir veri, meta veri altyapısı tarafından anlaşılan biçim dizisi olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="26bb1-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26bb1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26bb1-114">Requirements</span></span>  
 <span data-ttu-id="26bb1-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26bb1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26bb1-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="26bb1-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26bb1-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="26bb1-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="26bb1-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26bb1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26bb1-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26bb1-119">See Also</span></span>  
 [<span data-ttu-id="26bb1-120">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="26bb1-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="26bb1-121">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="26bb1-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
