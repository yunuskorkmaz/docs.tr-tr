---
title: IMetaDataImport::GetSigFromToken Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f40fb2e94eac13211cf8ccf179904071a23f59ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447233"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="54a98-102">IMetaDataImport::GetSigFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="54a98-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="54a98-103">Belirtilen belirteçle ilişkili ikili meta verileri imza alır.</span><span class="sxs-lookup"><span data-stu-id="54a98-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54a98-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54a98-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54a98-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54a98-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="54a98-106">[in] İkili meta veri imzası döndürülecek belirteci.</span><span class="sxs-lookup"><span data-stu-id="54a98-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="54a98-107">[out] Döndürülen meta veri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="54a98-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="54a98-108">[out] İkili meta verileri imza bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="54a98-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54a98-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54a98-109">Requirements</span></span>  
 <span data-ttu-id="54a98-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54a98-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54a98-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="54a98-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54a98-112">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="54a98-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="54a98-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54a98-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54a98-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54a98-114">See Also</span></span>  
 [<span data-ttu-id="54a98-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54a98-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="54a98-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54a98-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
