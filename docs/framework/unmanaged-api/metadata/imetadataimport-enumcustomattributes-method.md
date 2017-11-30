---
title: "IMetaDataImport::EnumCustomAttributes Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumCustomAttributes
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 78a642ab3c9766ba32537e24814b3b0536df67c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="167c1-102">IMetaDataImport::EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="167c1-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="167c1-103">Belirtilen tür veya üye ile ilişkili özel öznitelik tanımı belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="167c1-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="167c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="167c1-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="167c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="167c1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="167c1-106">[içinde out] Döndürülen Numaralandırıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="167c1-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="167c1-107">[in] Numaralandırma veya tüm özel öznitelikleri için sıfır kapsamı için bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="167c1-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="167c1-108">[in] Numaralandırılacak, özniteliklerin türü oluşturucusu için bir belirteç veya `null` tüm türleri.</span><span class="sxs-lookup"><span data-stu-id="167c1-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="167c1-109">[out] Özel öznitelik belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="167c1-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="167c1-110">[in] En büyük boyutunu `rCustomAttributes` dizi.</span><span class="sxs-lookup"><span data-stu-id="167c1-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="167c1-111">[out, isteğe bağlı] Döndürülen belirteç değerleri gerçek sayısını `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="167c1-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="167c1-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="167c1-112">Return Value</span></span>  
  
|<span data-ttu-id="167c1-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="167c1-113">HRESULT</span></span>|<span data-ttu-id="167c1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="167c1-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="167c1-115">`EnumCustomAttributes`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="167c1-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="167c1-116">Numaralandırılacak özel öznitelik vardır.</span><span class="sxs-lookup"><span data-stu-id="167c1-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="167c1-117">Bu durumda, `pcCustomAttributes` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="167c1-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="167c1-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="167c1-118">Requirements</span></span>  
 <span data-ttu-id="167c1-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="167c1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="167c1-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="167c1-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="167c1-121">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="167c1-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="167c1-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="167c1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="167c1-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="167c1-123">See Also</span></span>  
 [<span data-ttu-id="167c1-124">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="167c1-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="167c1-125">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="167c1-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
