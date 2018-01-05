---
title: "IMetaDataImport::EnumInterfaceImpls Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumInterfaceImpls
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 646d65ff81795ce0558651db9c3fe1bc7205ae08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="12d22-102">IMetaDataImport::EnumInterfaceImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12d22-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="12d22-103">Arabirim uygulamaları temsil eden MethodDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="12d22-103">Enumerates MethodDef tokens representing interface implementations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12d22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12d22-104">Syntax</span></span>  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12d22-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12d22-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="12d22-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="12d22-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="12d22-107">[in] Numaralandırılacak temsil eden arabirim uygulamaları, MethodDef belirteçler olan TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="12d22-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="12d22-108">[out] MethodDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="12d22-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="12d22-109">[in] En büyük boyutunu `rImpls` dizi.</span><span class="sxs-lookup"><span data-stu-id="12d22-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="12d22-110">[out] Döndürülen belirteçleri gerçek sayısını `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="12d22-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12d22-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="12d22-111">Return Value</span></span>  
  
|<span data-ttu-id="12d22-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="12d22-112">HRESULT</span></span>|<span data-ttu-id="12d22-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12d22-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="12d22-114">`EnumInterfaceImpls`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="12d22-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="12d22-115">Numaralandırılacak hiçbir MethodDef belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="12d22-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="12d22-116">Bu durumda, `pcImpls` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="12d22-116">In that case, `pcImpls` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12d22-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12d22-117">Requirements</span></span>  
 <span data-ttu-id="12d22-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12d22-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12d22-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="12d22-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12d22-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="12d22-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12d22-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12d22-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12d22-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12d22-122">See Also</span></span>  
 [<span data-ttu-id="12d22-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12d22-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="12d22-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12d22-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
