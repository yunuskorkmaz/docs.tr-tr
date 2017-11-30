---
title: "IMetaDataImport::IsValidToken Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.IsValidToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3c916e71518ded93c90b270205dd975201762846
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="eab61-102">IMetaDataImport::IsValidToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eab61-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="eab61-103">Belirtilen belirteç kodu nesnesi için geçerli bir başvuru tutan olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="eab61-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eab61-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eab61-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eab61-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="eab61-106">[in] Başvuru geçerliliğini denetlemek için belirteci.</span><span class="sxs-lookup"><span data-stu-id="eab61-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eab61-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="eab61-107">Return Value</span></span>  
 <span data-ttu-id="eab61-108">`true`varsa `tk` geçerli kapsam içinde geçerli meta veri belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="eab61-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="eab61-109">Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="eab61-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab61-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eab61-110">Requirements</span></span>  
 <span data-ttu-id="eab61-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eab61-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eab61-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eab61-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eab61-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="eab61-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eab61-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eab61-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab61-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eab61-115">See Also</span></span>  
 [<span data-ttu-id="eab61-116">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="eab61-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="eab61-117">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="eab61-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
