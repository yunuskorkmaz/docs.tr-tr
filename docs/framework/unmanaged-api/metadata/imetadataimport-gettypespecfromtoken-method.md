---
title: IMetaDataImport::GetTypeSpecFromToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeSpecFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 37a8c2580dad3e198290b72b49b0aacaf1804c25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="c12ec-102">IMetaDataImport::GetTypeSpecFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="c12ec-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="c12ec-103">Belirtilen belirteç tarafından temsil edilen tür belirtimi ikili meta verileri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="c12ec-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c12ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c12ec-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c12ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c12ec-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="c12ec-106">[in] İstenen meta veri imza ile ilişkili TypeSpec'te belirteci.</span><span class="sxs-lookup"><span data-stu-id="c12ec-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="c12ec-107">[out] İkili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c12ec-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="c12ec-108">[out] Meta veri imza bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c12ec-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c12ec-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c12ec-109">Return Value</span></span>  
 <span data-ttu-id="c12ec-110">Başarı veya başarısızlık gösterir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c12ec-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="c12ec-111">Hataları ile başarısız makrosu sınanabilir.</span><span class="sxs-lookup"><span data-stu-id="c12ec-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c12ec-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c12ec-112">Requirements</span></span>  
 <span data-ttu-id="c12ec-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c12ec-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c12ec-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c12ec-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c12ec-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c12ec-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c12ec-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c12ec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c12ec-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c12ec-117">See Also</span></span>  
 [<span data-ttu-id="c12ec-118">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="c12ec-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c12ec-119">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c12ec-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
