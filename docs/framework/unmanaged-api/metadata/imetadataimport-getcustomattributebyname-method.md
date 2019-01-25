---
title: IMetaDataImport::GetCustomAttributeByName Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68cac76a83164e24c0810c9d19fa845c8580b1d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637256"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="08eff-102">IMetaDataImport::GetCustomAttributeByName Metodu</span><span class="sxs-lookup"><span data-stu-id="08eff-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="08eff-103">Özel öznitelik adını ve sahibini verilen alır.</span><span class="sxs-lookup"><span data-stu-id="08eff-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08eff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08eff-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08eff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08eff-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="08eff-106">[in] Özel öznitelik sahip nesnesini temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="08eff-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="08eff-107">[in] Özel öznitelik adı.</span><span class="sxs-lookup"><span data-stu-id="08eff-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="08eff-108">[out] Özel öznitelik değeri olan verilerin bir dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="08eff-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="08eff-109">[out] Döndürülen verileri baytlık boyutu \*`ppData`.</span><span class="sxs-lookup"><span data-stu-id="08eff-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08eff-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08eff-110">Remarks</span></span>  
 <span data-ttu-id="08eff-111">Birden çok özel öznitelikler için aynı sahibi tanımlamak için geçerlidir; hatta aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="08eff-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="08eff-112">Ancak, `GetCustomAttributeByName` yalnızca bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="08eff-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="08eff-113">(`GetCustomAttributeByName` bulduğu ilk örneği döndürür.) Tüm özel öznitelik örneklerini bulmak için arama [Imetadataımport::enumcustomattributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="08eff-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08eff-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08eff-114">Requirements</span></span>  
 <span data-ttu-id="08eff-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08eff-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08eff-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="08eff-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08eff-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="08eff-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08eff-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08eff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08eff-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08eff-119">See also</span></span>
- [<span data-ttu-id="08eff-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08eff-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="08eff-121">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08eff-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
