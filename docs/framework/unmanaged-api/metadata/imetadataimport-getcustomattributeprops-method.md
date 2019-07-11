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
ms.openlocfilehash: c714915651d8660a739d8ee6518fc3814af4c08d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782409"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="0d0ac-102">IMetaDataImport::GetCustomAttributeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="0d0ac-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="0d0ac-103">Kendi meta veri belirteci verilen özel özniteliğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="0d0ac-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d0ac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d0ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d0ac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d0ac-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="0d0ac-106">[in] Alınacak özel öznitelik temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="0d0ac-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="0d0ac-107">[out, isteğe bağlı] Özel öznitelik değiştiren nesnesini temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="0d0ac-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="0d0ac-108">Bu değer, meta veri belirteci dışında herhangi bir türde olabilir `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="0d0ac-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="0d0ac-109">[out, isteğe bağlı] Bir `mdMethodDef` veya `mdMemberRef` meta veri belirteci temsil eden <xref:System.Type> döndürülen özel özniteliğinin.</span><span class="sxs-lookup"><span data-stu-id="0d0ac-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="0d0ac-110">[out, isteğe bağlı] Özel öznitelik değeri olan verilerin bir dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0d0ac-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="0d0ac-111">[out, isteğe bağlı] Döndürülen verileri baytlık boyutu \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="0d0ac-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d0ac-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d0ac-112">Remarks</span></span>  
 <span data-ttu-id="0d0ac-113">Özel bir öznitelik, bir veri, meta veri altyapısı tarafından anlaşılır biçimi dizisi olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="0d0ac-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d0ac-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d0ac-114">Requirements</span></span>  
 <span data-ttu-id="0d0ac-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d0ac-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d0ac-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0d0ac-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d0ac-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0d0ac-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d0ac-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d0ac-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d0ac-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d0ac-119">See also</span></span>

- [<span data-ttu-id="0d0ac-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d0ac-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0d0ac-121">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d0ac-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
