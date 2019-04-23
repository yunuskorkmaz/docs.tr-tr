---
title: IMetaDataImport::GetCustomAttributeProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c27a55166ebc055f324ec45ba6dfd835c8b8bbf6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075749"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="8d609-102">IMetaDataImport::GetCustomAttributeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="8d609-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="8d609-103">Kendi meta veri belirteci verilen özel özniteliğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="8d609-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d609-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d609-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d609-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d609-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="8d609-106">[in] Alınacak özel öznitelik temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="8d609-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="8d609-107">[out, isteğe bağlı] Özel öznitelik değiştiren nesnesini temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="8d609-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="8d609-108">Bu değer, meta veri belirteci dışında herhangi bir türde olabilir `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="8d609-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="8d609-109">[out, isteğe bağlı] Bir `mdMethodDef` veya `mdMemberRef` meta veri belirteci temsil eden <xref:System.Type> döndürülen özel özniteliğinin.</span><span class="sxs-lookup"><span data-stu-id="8d609-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="8d609-110">[out, isteğe bağlı] Özel öznitelik değeri olan verilerin bir dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8d609-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="8d609-111">[out, isteğe bağlı] Döndürülen verileri baytlık boyutu \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="8d609-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d609-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d609-112">Remarks</span></span>  
 <span data-ttu-id="8d609-113">Özel bir öznitelik, bir veri, meta veri altyapısı tarafından anlaşılır biçimi dizisi olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="8d609-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d609-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d609-114">Requirements</span></span>  
 <span data-ttu-id="8d609-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d609-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d609-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8d609-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d609-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8d609-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d609-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d609-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d609-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d609-119">See also</span></span>

- [<span data-ttu-id="8d609-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d609-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8d609-121">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d609-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
