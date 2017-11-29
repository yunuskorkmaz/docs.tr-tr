---
title: IMetaDataImport::GetCustomAttributeByName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetCustomAttributeByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b689c54b5e8d741d32bc941b4e78e6674f15e01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="d2d62-102">IMetaDataImport::GetCustomAttributeByName Metodu</span><span class="sxs-lookup"><span data-stu-id="d2d62-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="d2d62-103">Özel öznitelik adı ve sahibi verilen alır.</span><span class="sxs-lookup"><span data-stu-id="d2d62-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2d62-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2d62-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2d62-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2d62-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="d2d62-106">[in] Özel öznitelik sahibi nesnesini temsil eden bir meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="d2d62-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="d2d62-107">[in] Özel öznitelik adı.</span><span class="sxs-lookup"><span data-stu-id="d2d62-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="d2d62-108">[out] Bir özel öznitelik değeri veri dizisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d2d62-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="d2d62-109">[out] Döndürülen verileri bayt cinsinden boyutu *`ppData`.</span><span class="sxs-lookup"><span data-stu-id="d2d62-109">[out] The size in bytes of the data returned in *`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2d62-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2d62-110">Remarks</span></span>  
 <span data-ttu-id="d2d62-111">Birden çok özel öznitelikleri için aynı sahibi tanımlamak için uygundur; bile aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="d2d62-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="d2d62-112">Ancak, `GetCustomAttributeByName` yalnızca bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d2d62-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="d2d62-113">(`GetCustomAttributeByName` bulduğu ilk örneğini döndürür.) Özel bir öznitelik tüm örneklerini bulmak için arama [Imetadataımport::enumcustomattributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2d62-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2d62-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2d62-114">Requirements</span></span>  
 <span data-ttu-id="d2d62-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2d62-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2d62-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d2d62-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2d62-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d2d62-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2d62-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2d62-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d62-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2d62-119">See Also</span></span>  
 [<span data-ttu-id="d2d62-120">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2d62-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d2d62-121">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2d62-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
