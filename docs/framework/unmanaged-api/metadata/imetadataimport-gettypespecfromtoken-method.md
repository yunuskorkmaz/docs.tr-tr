---
title: IMetaDataImport::GetTypeSpecFromToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 10d4d9dcad2494410cc361617d5292c519b6dc00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="1efb8-102">IMetaDataImport::GetTypeSpecFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="1efb8-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="1efb8-103">Belirtilen belirteç tarafından temsil edilen tür belirtimi ikili meta verileri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="1efb8-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1efb8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1efb8-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1efb8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1efb8-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="1efb8-106">[in] İstenen meta veri imza ile ilişkili TypeSpec'te belirteci.</span><span class="sxs-lookup"><span data-stu-id="1efb8-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="1efb8-107">[out] İkili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1efb8-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="1efb8-108">[out] Meta veri imza bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="1efb8-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1efb8-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1efb8-109">Return Value</span></span>  
 <span data-ttu-id="1efb8-110">Başarı veya başarısızlık gösterir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1efb8-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="1efb8-111">Hataları ile başarısız makrosu sınanabilir.</span><span class="sxs-lookup"><span data-stu-id="1efb8-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1efb8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1efb8-112">Requirements</span></span>  
 <span data-ttu-id="1efb8-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1efb8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1efb8-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1efb8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1efb8-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1efb8-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1efb8-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1efb8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1efb8-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1efb8-117">See Also</span></span>  
 [<span data-ttu-id="1efb8-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1efb8-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1efb8-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1efb8-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
